<template>

  <div>
    <div class="theGame">
      <div class="title">
        <h1>Test Your Reaction<br>
         Wait tell the blue circle to appear</h1>
         <button @click.prevent="play" :disabled="isPlaying">Start Game</button>
      </div>

      <block 
        :delayGame="delay"
        :top="top"
        :right="right"
        v-if="isPlaying"
        @stopTi="endGame"
        class="position"
      />
      <div class="afterGame" v-if="score != null" >
        <result
          :reaction="score"
          v-if="score != null"
        />

        <info
          :scoreto="score"
          @pushInfo="addHistory"
          v-if="score != null"
        
        />
      </div>
    </div>    
    <hist
      :HistoryOfplayer="history"
    />

    <div>
      <h1 style="color:black;">Hello</h1>
      <ul>
        <li v-for="jober in jobs" :key="jober.id" > {{jober.title}} </li>
      </ul>
      
    </div>
    
  </div>
  
</template>

<script>
 import block  from './components/Blok.vue'
 import result  from './components/Result.vue'
 import info  from './components/Info.vue'
 import hist  from './components/History.vue'

export default {
  name: 'App',
  components: {
    block,result,info,hist
  },
  data () {
    return {
      isPlaying: false,
      delay: null,
      score:null,
      top:null,
      right:null,
      history:[],
      jobs:[],
    }
  },
  mounted(){
    fetch('http://localhost:3000/jobs')
      .then(res => res.json())
      .then(data => this.jobs = data)
      .catch(err => console.log(err.message))
  },
  methods:{
    play() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true;
      
      this.score = null;
      this.top= 87 - Math.floor(Math.random() * 87);
      this.right= 87 - Math.floor(Math.random() * 87);

    },
    endGame(timer){
      this.score = timer;
      this.isPlaying = false;
      //console.log(this.score);
    },
    addHistory(x){
      this.history = x;
    }
  },
 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  
  margin-top: 60px;
}
.afterGame{
    width: 30%;
    padding-bottom: 40px;
    line-height: 26px;
    -webkit-box-shadow: 5px 5px 15px 5px rgba(206,206,206,0.69); 
    box-shadow: 5px 5px 15px 5px rgba(206,206,206,0.69);
    margin: 50px auto;
}
h1{
  text-transform: capitalize;
  font-size: 30px;
  color: #2196F3; 
  line-height: 30px; 
}
button{
  background: tomato;
  border: none;
  color: white;
  padding: 10px 30px;
  font-size: 14px;
  text-transform: uppercase;
  border-radius: 10px;
  cursor: pointer;
}
button[disabled]{
  background: gray;
}

</style>
