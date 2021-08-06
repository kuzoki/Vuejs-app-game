<template>
  <div >
    <form class="form" v-on:submit.prevent="pushToHistory(player.name,player.email)">
        <input type="text" placeholder="Your name" required v-model="player.name">
        <input type="email" placeholder="info@mail.com" v-model="player.email">
        <button type="submit" class="submit" :disabled="stateOf">submit</button>
    </form>
    
  </div>
</template>

<script>
export default {
    props:['scoreto','state'],
    data () {
        return {
            stateOf:this.state,
            player:
                { 
                    name: '',
                    email:'',
                }, 
            scorHistory:[],
        }
    },
    methods:{
        pushToHistory(name,email){
            this.scorHistory.push({
                name: name,
                email: email,
                score: this.scoreto
            });
            
            this.stateOf = true,
            this.$emit('pushInfo', this.scorHistory);
            
        }
    }
}
</script>

<style>
.form{
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    margin-top: 20px;
}
input{
    margin-bottom: 10px;
    padding: 10px 30px;
    width: 300px;
    margin: 0 auto 10px;
    
}
.submit{
    background:green;
    padding: 10px 40px;
    display: block;
    color: white;
    margin: 0 auto 10px;
}
</style>