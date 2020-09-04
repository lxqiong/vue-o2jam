<template>
    <div id="music_1">
        <div v-for="(item,index) in channles" :key="channles+index" class="music_channle">
            <BlockChannel :show="showchannel[item]" :id='"channel"+channles[index]'></BlockChannel>
        </div>
      </div>
</template>

<script>
import BlockChannel from "./BlockChannel"
export default {
    name:'Block',
    data:function(){
        return {
             channles: [1, 2, 3, 4, 5, 6, 7],
             showchannel:[false,false,false,false,false,false,false,false],
        }
    },
    props:{
        show:{
            type:Boolean,
            required:true
        }
    },
    watch:{
        show:function(val){
            console.log("show block vue ")
            console.log(this)
           this.$set(this.showchannel,2,val)
            
        }
    },
    components:{
        BlockChannel,
    },
    
}
</script>

<style lang="less" scoped>
     .rectangle_color{
         background-color: yellow;
     }
    //  .rectangle_color{
    //      background-color: yellow;
    //  }


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
        .rectangle_color;
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
         .rectangle_color;
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
         .rectangle_color;
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
         .rectangle_color;
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
        .rectangle_color;
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
         .rectangle_color;
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
</style>