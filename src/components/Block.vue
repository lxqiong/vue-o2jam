<template>
    <div id="music_1">
        <div v-for="(item,index) in channles" :key="channles+index" class="music_channle" >
            <BlockChannel :show="showchannel[item]" :id='"channel"+channles[index]' :channelName='channles[index]' v-on:showdone="handledone"></BlockChannel>
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
            type:Array,
            required:true
        }
    },
    watch:{
        show:function(arrayval){
          console.log("Block:"+arrayval)
          console.log(this)
          arrayval.forEach((value,index) => {
              console.log("show block vue "+index+" "+value)
            this.$set(this.showchannel,index,value)  
          });
        },
    },
    methods:{
       handledone(val){
         if(this.$store.state.isplay==false){
           return;
         }
        console.log("handledone:"+val)
        this.$set(this.showchannel,val,false)  
        this.$store.state.isshow[val]=false
        setTimeout(()=>{
          this.$set(this.showchannel,val,true)
          this.$store.state.isshow[val]=true
        },1000)
           
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
    }
</style>