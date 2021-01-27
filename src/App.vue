<template>
  <div id="app">
    <Card :card="{value: 7, suite: 'Clubs'}" face-down />
    <Card :card="{value: 13, suite: 'Spades'}" />
    <Deck :cards="topFive" />


  </div>
</template>

<script>
import Card from '@/components/Card'
import Deck from '@/components/Deck'

Array.prototype.shuffle = function(){
  return this.sort(() => Math.random()-0.5 )
}

export default {
  name: 'App',
  components: {Card, Deck},
  data(){ return {
    deck: []
  }},
  computed: {
    topFive(){
      return this.deck.filter((_,i) => i<5)
    }
  },


  created(){
    const suites = ["Hearts", "Spades", "Diamonds", "Clubs"]
    for(let suite of suites){
      for(let value = 1; value <= 13; value++){
        const card = {suite, value}
        this.deck.push(card)
      }
    }

    this.deck = this.deck.shuffle()
  }
}
</script>

<style lang="scss">
body,html,#app{ height: 100%; margin: 0; padding: 0;}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: grey;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
