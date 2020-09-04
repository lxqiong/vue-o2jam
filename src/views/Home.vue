<template>
  <div class="home">
    <div id="music">
      <Block :show="isshow"></Block>
      <div id="music_2">
        <div id="keyboard_1" class="sinkeyborad" @click="handle_s">
          S
          <div class="rightcorner">
          </div>
        </div>
        <div id="keyboard_2" class="evenkeyborad" @click="handle_d">D</div>
        <div id="keyboard_3" class="sinkeyborad" @click="handle_f">
          <div class="leftcorner"></div>
          <div class="rightcorner"></div>F
        </div>
        <div id="keyboard_4" class="evenkeyborad" @click="handle_spa">spa</div>
        <div id="keyboard_5" class="sinkeyborad"  @click="handle_j">
          <div class="leftcorner"></div>
          <div class="rightcorner"></div>J
        </div>
        <div id="keyboard_6" class="evenkeyborad" @click="handle_k">K</div>
        <div id="keyboard_7" class="sinkeyborad" @click="handle_l">
          <div class="leftcorner"></div>L
        </div>
      </div>
      <div id="music_3">
        <TypeButton
          @click="gamestart"
          class="gamestart"
          type="defaul"
          v-on:restart="gamestart"
        >游戏开始</TypeButton>
      </div>
    </div>
    <div id="content">bb</div>
  </div>
</template>

<script>
import TypeButton from "../components/TypeButton";
import Block from "../components/Block"

export default {
  name: "Home",
  components: {
    TypeButton,
    Block,
  },
  data: function () {
    return {
      isshow: false,
    };
  },
  methods: {
    gamestart: function () {
      console.log("111");
      this.isshow = true;
      return;
    },
    handle_s:function(){
      console.log("handle_s");
       var keys = document.getElementById("keyboard_1");
        keys.style="animation: ripple 1s";
        setTimeout(function(){
          keys.style="animation: none";
        },1000)
    },
    handle_d:function(){
      console.log("handle_d");
       var keys = document.getElementById("keyboard_2");
        keys.style="animation: ripple 1s";
        setTimeout(function(){
          keys.style="animation: none";
        },1000)
        this.isshow = false;
        setTimeout(()=>{
          this.isshow = true;
        },0);
    },
    handle_f:function(){
      console.log("handle_f");
       var keys = document.getElementById("keyboard_3");
        keys.style="animation: ripple 1s";
        setTimeout(function(){
          keys.style="animation: none";
        },1000)
    },
    handle_spa:function(){
      console.log("handle_spa");
       var keys = document.getElementById("keyboard_4");
        keys.style="animation: ripple 1s";
        setTimeout(()=>{
          keys.style="animation: none";
        },1000)
    },
    handle_j:function(){
      console.log("handle_j");
       var keys = document.getElementById("keyboard_5");
        keys.style="animation: ripple 1s";
        setTimeout(function(){
          keys.style="animation: none";
        },1000)
    },
    handle_k:function(){
      console.log("handle_k");
       var keys = document.getElementById("keyboard_6");
        keys.style="animation: ripple 1s";
        setTimeout(function(){
          keys.style="animation: none";
        },1000)
    },
     handle_l:function(){
      console.log("handle_l");
       var keys = document.getElementById("keyboard_7");
        keys.style="animation: ripple 1s";
        setTimeout(function(){
          keys.style="animation: none";
        },1000)
    },

  },
  created() {
    console.log("created");
    console.log(this);
    document.onkeydown = () => {
      var key = window.event.keyCode;
      if (key == 32) {
        this.handle_spa();
      } else if (key == 83) {
        this.handle_s();
      }else if(key==70){
        this.handle_f();
      }else if(key==68){
        this.handle_d();
      }else if(key==74){
        this.handle_j();
      }else if(key==75){
        this.handle_k();
      }else if(key==76){
         this.handle_l();
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
  }
  #music_2 {
    display: flex;
    height: 7%;
    justify-content: space-between;

    background-color: black;
    .sinkeyborad {
      display: flex;
      width: 100%;
      position: relative;
      background-color: #676767;
      border: 2px solid black;
      align-items: center;
      justify-content: center;
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
