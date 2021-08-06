<template>
  <div class="history">
      <h1>Your Score History</h1>
        <ul>
            <li v-for="(item, index) in HistoryOfplayer" :key="index">{{HistoryOfplayer[index].name}} : {{HistoryOfplayer[index].score}} <span>ms</span> </li>
        </ul>
    
  </div>
</template>

<script>
export default {
    props:['HistoryOfplayer',], 
    
}
</script>

<style>
    body{
        position: relative;
    }
    .history{
        text-align: left;
        position: absolute;
        top: 0px;
        left: 10px;
        padding: 20px;
        width: 350px;
        letter-spacing: 0.5px;
        text-transform: uppercase;
        line-height: 26px;
        box-shadow: 5px 5px 15px 5px rgba(236, 236, 236, 0.69);;
    }
    .history h1{
        font-size: 15px;
        color: black;
    }
    ul{
        padding: 0;
    }
    li{
        list-style: none;
        font-size: 12px;
        text-transform: uppercase;
    }
    li span{
        text-transform: lowercase;
    }
</style>