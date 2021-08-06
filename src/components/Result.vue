<template>
  <div class="result">
      Your Reaction Time Is :  <span>{{reaction}} ms</span> 
      <div v-if="reaction > 1000 ">"You are Very Slow turtule" </div>
      <div v-if="reaction > 500 && reaction < 1000 "> "The Eye Of Cat"</div>
      <div v-if="reaction > 300 && reaction < 500 ">"Fast Like A Lion"</div>
      <div v-if=" reaction < 300 ">"Hello To The Devil"</div>
  </div>
</template>

<script>
export default {
    props:['reaction'],    
}
</script>

<style>
.result{
    padding: 40px 0;
    background: rgb(255, 255, 255);
    border-radius: 10px;
    font-size: 15px;
    letter-spacing: 0.5px;
    text-transform: uppercase;
    line-height: 26px;
    font-weight: 600;
   
}
.result span{
    font-size: 15px;
    text-transform: capitalize;
}
</style>