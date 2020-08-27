<template>
  <div class="home">
    <div id="music">
      <div id="music_1">
        <div v-for="(item,index) in channles" :key='"channles"+index' class="music_channle">

        </div>
      </div>
     <div id="music_2">
        <div id="keyboard_1" class="sinkeyborad" >
          S
          <div class="rightcorner">
          </div>
        </div>
        <div id="keyboard_2" class="evenkeyborad">
          D
        </div>
        <div id="keyboard_3" class="sinkeyborad">
           <div class="leftcorner">
          </div>
          <div class="rightcorner">
          </div>
          F
        </div>
        <div id="keyboard_4" class="evenkeyborad">
          spa
        </div>
        <div id="keyboard_5" class="sinkeyborad">
           <div class="leftcorner">
          </div>
           <div class="rightcorner">
          </div>
          J
        </div>
        <div id="keyboard_6" class="evenkeyborad">
          K
        </div>
        <div id="keyboard_7" class="sinkeyborad">
           <div class="leftcorner">
          </div>
          L
        </div>
      </div>
      <div id="music_3">
         <TypeButton  @click="gamestart1" class="gamestart" type="defaul">游戏开始</TypeButton>  
      </div>
    </div>
    <div id="content">
      bb
    </div>
    
  </div>
</template>

<script>

import TypeButton from '../components/TypeButton'

export default {
  name: 'Home',
  components: {
    TypeButton,

  },
  data:function(){
    
    return {
      channles:[1,2,3,4,5,6,7],
      show:false,
    } 
  },
  methods:{
    gamestart1:function (){
      console.log("111");
      this.show=true;
      return;
    },
  }

}
</script>

<style lang="less">

@keyframes ripple{
    from {
        transform:translate(10%,10%) scale(0);
        background: rgba(255,0,0,.75);
    }
    to {
        transform:translate(10%,10%) scale(2);
        background: transparent;
    }
}

.fade-enter-active, .fade-leave-active {
          transition: opacity .5s;
        }
        .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
          opacity: 0;
        }

.home{
  display: flex;
  width: 100%;
  height: 100%;
}

#music{
  height: 100%;
  width: 30%;
  background-color: red;
  display: flex;
  flex-direction: column;
  #music_1{
    display: flex;
    height: 85%;
    justify-content: space-between;
    background-color: black;
    position: relative;
    .music_channle{
      display: flex;
     width: 100%;
     height: 100%;
      border:1px solid red;
      position: relative;
    }
  }
  #music_2{
    display: flex;
    height: 7%;
    justify-content: space-between;
   
    background-color: black;
    .sinkeyborad{
      display: flex;
      width: 100%;
      position: relative;
      background-color: #676767;
       border: 2px solid black;
      align-items: center;
      justify-content:center;
      &:active{
       animation: ripple 1s;
      
      }
      
    }
    .evenkeyborad{
      display: flex;
      width: 100%;
      position: relative;
      background-color: #8f8f8f;
      border-top: 2px solid black;
      // border-right: 1px solid black;
      border-bottom: 2px solid black;
       align-items: center;
      justify-content:center;
    }
    .leftcorner{
      position: absolute;
      height: 25%;
      width: calc(50% + 2px);
      left: -2px;
      bottom: 0px;
      background-color: #8f8f8f;
      border-top:2px solid black;
      border-right:2px solid black;
    }
    .rightcorner{
      position: absolute;
      height: 25%;
      width: calc(50% + 2px);
      right: -2px;
      bottom: 0px;
      border-top:2px solid black;;
      border-left:2px solid black;
      background-color: #8f8f8f;
    }
  }
  #music_3{
    display: flex;
    justify-content:center;
    height: 8%;
    background: black; 
    text-align: center; 
     align-items: center;
    .gamestart{ 
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
        text-align:center; 
        align-items: center;
        box-sizing: border-box;
       
      }
  }
}


#content{
   height: 100%;
  width: 70%;
  background-color: yellow;
  display: flex;
}

</style>
