<template>
  <div class="block-warp">
    <div class="block" v-show="showBlock" @click="stopTimer"  ref="noname">
        
    </div>
    
  </div>
    

     
</template>

<script>
export default {
    props:['delayGame','top','right'],
    data(){
        return{
            showBlock :false,
            timer:null,
            reactionTime: 0,
        }
    },
    
    mounted(){
        setTimeout(()=>{
            this.showBlock = true;
            this.startTimer();
            //console.log(this.$refs.noname) ;
            this.$refs.noname.style.top = this.top + '%';
            this.$refs.noname.style.right = this.right + '%';
        },this.delayGame)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime += 10;
                
            },10); 
            
        },

        stopTimer(){
            clearInterval(this.timer);
            this.$emit('stopTi', this.reactionTime);
        }
    },
   
}
</script>

<style>
    .block{
        width: 50px;
        height: 50px;
        border-radius: 50%;
        background:teal;
        /* margin: 50px auto; */
        text-align: center;
        display: block;
        color: white;
        cursor: pointer;
        position:absolute;
    }
    .block-warp{
        width: 500px;
        height: 400px;
        background:whitesmoke;
        margin: 50px auto;
        padding: 5px;
       position: relative;
    }
   
</style>