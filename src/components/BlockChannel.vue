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
             isshow:false
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
            if(val==false){
                 this.isfires=!val;
            }else{
                this.isshow=val;
            }
            console.log("show block:"+this.isshow+" is fires:"+this.isfires)
           
        }
    },

    methods:{
            transitionComplete: function (e) {
            console.log("transitionComplete:");
             console.log(e)
             if(e.animationName=="recdown"){
                 this.isfires = true;
             }else if(e.animationName=="secondrightbomb"){
                 this.isshow = false;
                  setTimeout(() => {
                console.log("restart");
                console.log(this);
                this.isshow = true;
                this.isfires = false;
                }, 0);

             }
        },
        transitionStart: function () {
            console.log("transitionStart")
            console.log(document.getElementById("channel2").className) ;
            var cls = document.getElementById("channel2").className;
            cls +=" rectangle_color";
            document.getElementById("channel2").className=cls;
            console.log(document.getElementById("channel2").className) ;
        },
    }

}
</script>

<style>

</style>