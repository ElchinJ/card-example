<template>
  <section> 
    <div id="app">
      <!-- <ActionBar/> -->
      <Card :card="{value: 7, suite: 'Clubs'}"/>
      <!-- <Card :card="{value: 13, suite: 'Spades'}" faceDown/> -->
      <Deck :cards="topFive" faceDown/>
      <!-- <Score/> -->
    </div>
  </section>
</template>

<script>
import Card from '@/components/Card'
import Deck from '@/components/Deck'
//import Score from '@/components/Score'
//import ActionBar from '@/components/ActionBar'

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
      return this.deck.filter((_,i) => i < 5)
    }
  },
  created() {
    const suites = ["Hearts", "Spades", "Diamonds", "Clubs"]
    for(let suite of suites){
      for(let value = 1; value <= 13; value++) {
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
  background-color: green;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
