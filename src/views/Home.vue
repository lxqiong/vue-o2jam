<template>
  <div class="home">
    <div id="music">
      <div id="music_1">
        <div v-for="(item,index) in channles" :key="channles+index" class="music_channle">
          <div class="rectangle" v-if="show" @animationend="transitionComplete">
            <div class="fires" v-if="isfires">
              <div class="leftfire"></div>
              <div class="middlefire"></div>
              <div class="rightfire"></div>
              <div class="secondleftfire"></div>
              <div class="secondmiddlefire"></div>
              <div class="secondrightfire"></div>
            </div>
          </div>
        </div>
      </div>
      <div id="music_2">
        <div id="keyboard_1" class="sinkeyborad" @click="handle_s">
          S
          <!-- <div class="rightcorner">
          </div>-->
        </div>
        <div id="keyboard_2" class="evenkeyborad">D</div>
        <div id="keyboard_3" class="sinkeyborad">
          <div class="leftcorner"></div>
          <div class="rightcorner"></div>F
        </div>
        <div id="keyboard_4" class="evenkeyborad" @keyup.enter="recvspace">spa</div>
        <div id="keyboard_5" class="sinkeyborad">
          <div class="leftcorner"></div>
          <div class="rightcorner"></div>J
        </div>
        <div id="keyboard_6" class="evenkeyborad">K</div>
        <div id="keyboard_7" class="sinkeyborad">
          <div class="leftcorner"></div>L
        </div>
      </div>
      <div id="music_3">
        <TypeButton
          @click="gamestart1"
          class="gamestart"
          type="defaul"
          v-on:restart="gamestart1"
        >游戏开始</TypeButton>
      </div>
    </div>
    <div id="content">bb</div>
  </div>
</template>

<script>
import TypeButton from "../components/TypeButton";

export default {
  name: "Home",
  components: {
    TypeButton,
  },
  data: function () {
    return {
      channles: [1, 2, 3, 4, 5, 6, 7],
      show: false,
      isfires: false,
      icount: 0,
    };
  },
  methods: {
    gamestart1: function () {
      console.log("111");
      this.isfires = false;
      this.show = true;
      return;
    },
    recvspace: function () {
      console.log("space");
    },
    transitionComplete: function () {
      console.log("transitionComplete");
      this.icount++;
      this.isfires = true;
      if (this.icount && this.icount % 49 == 0) {
        this.show = false;
        this.isfires = true;
        setTimeout(() => {
          console.log("restart");
          console.log(this);
          this.gamestart1();
        }, 0);
      }
    },
    afterfires: function () {
      console.log("afterfires");
      // this.isfires=false;
      this.show = true;
    },
    handle_s:function(){
      console.log("handle_s");
       var keys = document.getElementById("keyboard_1");
        keys.style="animation: ripple 1s";
        keys.style.display;
        setTimeout(function(){
          keys.style="animation: none";

        },1000)
    }
  },
  created() {
    console.log("created");
    document.onkeydown = () => {
      var key = window.event.keyCode;
      if (key == 32) {
        console.log("空格");
      } else if (key == 83) {
        console.log("s");
        this.handle_s();
      }
    };
  },
};
</script>

<style lang="less">
@keyframes ripple {
  from {
    transform: translate(10%, 10%) scale(0);
    background: rgba(255, 0, 0, 0.75);
  }
  to {
    transform: translate(10%, 10%) scale(2);
    background: transparent;
  }
}

.home {
  display: flex;
  width: 100%;
  height: 100%;
}

#music {
  height: 100%;
  width: 30%;
  background-color: red;
  display: flex;
  flex-direction: column;
  #music_1 {
    display: flex;
    height: 85%;
    justify-content: space-between;
    background-color: black;
    position: relative;
    @keycolor: aqua;
    .music_channle {
      display: flex;
      width: 100%;
      height: 100%;
      border: 1px solid red;
      position: relative;
      justify-content: center;
      .rectangle {
        width: 90%;
        height: 2%;
        background-color: @keycolor;
        position: relative;
        animation: recdown 5s;
        animation-fill-mode: forwards;
        opacity: 1;
      }
      @keyframes recdown {
        to {
          transform: translateY(calc(768px * 0.83));
          opacity: 0.3;
        }
      }
      .leftfire {
        width: 33%;
        height: 50%;
        background-color: @keycolor;
        animation: leftbomb 1s;
        position: absolute;
        top: 0;
        left: 0;
        animation-fill-mode: forwards;
        opacity: 1;
      }
      .middlefire {
        width: 33%;
        height: 50%;
        background-color: @keycolor;
        animation: middlebomb 1s;
        position: absolute;
        top: 0;
        left: 33%;
        animation-fill-mode: forwards;
        opacity: 1;
      }
      .rightfire {
        width: 33%;
        height: 50%;
        background-color: @keycolor;
        animation: rightbomb 1s;
        position: absolute;
        top: 0;
        right: 0;
        animation-fill-mode: forwards;
        opacity: 1;
      }
      .secondleftfire {
        width: 33%;
        height: 50%;
        background-color: @keycolor;
        animation: secondleftbomb 1s;
        position: absolute;
        left: 0;
        bottom: 0;
        animation-fill-mode: forwards;
        opacity: 1;
      }
      .secondmiddlefire {
        width: 33%;
        height: 50%;
        background-color: @keycolor;
        animation: secondmiddlebomb 1s;
        position: absolute;
        bottom: 0;
        left: 33%;
        animation-fill-mode: forwards;
        opacity: 1;
      }
      .secondrightfire {
        width: 33%;
        height: 50%;
        background-color: @keycolor;
        animation: secondrightbomb 1s;
        position: absolute;
        bottom: 0;
        right: 0;
        animation-fill-mode: forwards;
        opacity: 1;
      }
      @keyframes leftbomb {
        to {
          transform: translate(-10px, -10px);
          opacity: 0;
          border-radius: 2px;
        }
      }
      @keyframes middlebomb {
        to {
          transform: translate(0, -10px);
          opacity: 0;
          border-radius: 2px;
        }
      }
      @keyframes rightbomb {
        to {
          transform: translate(10px, -10px);
          opacity: 0;
          border-radius: 2px;
        }
      }
      @keyframes secondleftbomb {
        to {
          transform: translate(-10px, 10px) scale(2);
          opacity: 0;
          border-radius: 2px;
        }
      }
      @keyframes secondmiddlebomb {
        to {
          transform: translate(0, 10px);
          opacity: 0;
          border-radius: 2px;
        }
      }
      @keyframes secondrightbomb {
        to {
          transform: translate(10px, 10px);
          opacity: 0;
          border-radius: 2px;
        }
      }
    }
  }
  #music_2 {
    display: flex;
    height: 7%;
    justify-content: space-between;

    background-color: black;
    // #keyboard_1{
    //   animation: ripple 1s;
    // }
    .sinkeyborad {
      display: flex;
      width: 100%;
      position: relative;
      background-color: #676767;
      border: 2px solid black;
      align-items: center;
      justify-content: center;
      
      // &:active {
      //   animation: ripple 1s;
      // }
    }
    .evenkeyborad {
      display: flex;
      width: 100%;
      position: relative;
      background-color: #8f8f8f;
      border-top: 2px solid black;
      // border-right: 1px solid black;
      border-bottom: 2px solid black;
      align-items: center;
      justify-content: center;
    }
    .leftcorner {
      position: absolute;
      height: 25%;
      width: calc(50% + 2px);
      left: -2px;
      bottom: 0px;
      background-color: #8f8f8f;
      border-top: 2px solid black;
      border-right: 2px solid black;
    }
    .rightcorner {
      position: absolute;
      height: 25%;
      width: calc(50% + 2px);
      right: -2px;
      bottom: 0px;
      border-top: 2px solid black;
      border-left: 2px solid black;
      background-color: #8f8f8f;
    }
  }
  #music_3 {
    display: flex;
    justify-content: center;
    height: 8%;
    background: black;
    text-align: center;
    align-items: center;
    .gamestart {
      flex-direction: column;
      display: inline-block;
      width: 80%;
      outline: 0;
      overflow: hidden;
      position: relative;
      cursor: pointer;
      user-select: none;
      line-height: 100%;
      font-size: 30px;
      background: #8f8f8f;
      border-radius: 10px;
      text-align: center;
      align-items: center;
      box-sizing: border-box;
    }
  }
}

#content {
  height: 100%;
  width: 70%;
  background-color: yellow;
  display: flex;
}
</style>
