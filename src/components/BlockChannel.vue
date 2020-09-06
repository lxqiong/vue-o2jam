<template>
    <div class="rectangle" @animationstart="transitionStart" @animationend="transitionComplete" v-if="isshow">
        <div class="fires" v-if="isfires">
            <div class="leftfire"></div>
            <div class="middlefire"></div>
            <div class="rightfire"></div>
            <div class="secondleftfire"></div>
            <div class="secondmiddlefire"></div>
            <div class="secondrightfire"></div>
        </div>
    </div>
</template>


<script>

export default {
    name:'BlockChannel',
    data:function(){
        return {
            isfires:false,
            isshow:false,
        }
    },

    props:{
        show:{
            type:Boolean,
            required:true
        },
        channelName:{
            type:Number,
            equired:true
        }
    },
    watch:{
        show:function(val){
           
            var channelName = "channel"+this.channelName
            console.log("blockchannel: "+channelName+" :"+val)
            var element = document.getElementById(channelName);
            if(val==false){
                
                if(this.isshow==true){
                    if(this.isfires==false && this.$store.state.isplay){
                        console.log("击中")
                        this.$store.state.score++;
                    }
                    this.$store.state.isshow[this.channelName]=false
                    this.isfires=true;
                    document.getElementById(channelName).style.animationPlayState="paused";
                    document.getElementById(channelName).style.opacity="0.3";
                    
                    
                }
            }else{
                this.isshow=val;
                this.isfires=false;
                if(element)
                    element.style.display="block";
            }
            
            console.log("show blockchannel:"+this.isshow+" is fires:"+this.isfires)  
        },
        channelName:function(val){
            console.log("channelName:"+val)
        }
    },

    methods:{
            transitionComplete: function(e){
             if(e.animationName.includes("recdown")){
                 this.isfires = true;
             }else if(e.animationName.includes("secondrightbomb")){
                 this.isshow = false;
                  setTimeout(() => {
                console.log("restart:"+this.channelName);
                this.isshow = false;
                this.isfires = false;
                this.$store.state.isshow[this.channelName]=false;
                this.$emit("showdone",this.channelName);
                console.log(this)
                
                }, 0);

             }
        },
        transitionStart: function () {
           // console.log("transitionStart")
           // console.log(this.channelName);
            var channelName = "channel"+this.channelName
           // console.log(document.getElementById(channelName))
            var cls = document.getElementById(channelName).className;
            if(cls.includes("rectangle_color")==false){
                cls +=" rectangle_color";
            }
            document.getElementById(channelName).className=cls;
            
            
        },
    }

}
</script>

<style lang="less" scoped>

      .leftfire {
        width: 33%;
        height: 50%;
        // .rectangle_color;
        background-color: yellow;
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
        //  .rectangle_color;
        background-color: yellow;
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
        //  .rectangle_color;
        background-color: yellow;
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
        //  .rectangle_color;
        background-color: yellow;
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
        // .rectangle_color;
        background-color: yellow;
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
        //  .rectangle_color;
        background-color: yellow;
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

</style>