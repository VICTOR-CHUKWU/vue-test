<template>
  <div class="hello">
    <h3 v-if="isUserWon">Congratulations you won the game</h3>
   <div  class=" card-row">
    <div v-for="(game, index) in gameNumbers" :key="index">
      <Card  :gameNumber="game"/>
    </div>
   </div>
    <div>
      <p>Input your game value here</p>
      <input type="text" v-model="userInput">
      <button @click="getNumber">Submit</button>
    </div>
   
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Card from './Card.vue'

export default defineComponent({
  name: 'HelloWorld',
  components: {Card},
  data() {
    return {
      gameNumbers:[0,0,0],
      userInput: '',
      isUserWon: false
    }
  },
  methods: {
    getNumber() {
      this.gameNumbers = [0,0,0]
      this.isUserWon = false
      for(let i = 0; i< 3; i++){
        const numberset = Math.round(Math.random() * 10)
        this.gameNumbers[i] = numberset

      }
      let total = 0

      for(let i = 0; i< this.gameNumbers.length; i++){
        total += this.gameNumbers[i]
        if(this.gameNumbers[i] === Number(this.userInput)){
          this.isUserWon = true
          break;
        }
        if(total === Number(this.userInput)){
          this.isUserWon = true
          break;
        }
        for(let j = i + 1; j < this.gameNumbers.length; j++){
          if(this.gameNumbers[i] + this.gameNumbers[j] === Number(this.userInput)){
            this.isUserWon = true
          break;
          }
        }

      }
      
    }
  }
});
</script>

<style scoped>
.card-row {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}
h3 {
  margin: 40px 0 0;
  color: green;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
