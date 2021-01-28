<template>
  <section> 
    <Score id="score"/>
    <div id="app">
      <Card id="card" :card="{value, suite}"/>
      <Deck id="deck" :cards="topFive" faceDown/> 
    </div>
    <hr>
    <ActionBar id="actionBar" @turn='guessLower'/>
  </section>
</template>

<script>
import Card from '@/components/Card'
import Deck from '@/components/Deck'
import Score from '@/components/Score'
import ActionBar from '@/components/ActionBar'

export default {
  name: 'App',
  components: {Card, Deck, Score, ActionBar},

  data(){ return {
    deck: [],
    value: 6,
    suite: 'Hearts',
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
  },
  // mounted() {
  //   this.Game = new Game()
  // },
  methods: {
    guessLower() {
      let nextCard = this.deck[0].value
      console.log('Check if facedown', Deck.faceDown)
      if(this.value > nextCard.value){
        console.log('Du gissade rätt!!!');
      }
    },
    guessSame(){

    }
}
}
</script>

<style lang="scss">
body,html,#app{ height: 100%; margin: 0; padding: 0;}

section {
  display: flex;
  flex-direction: column; 
  background-color: green;
}

#app {
  display: flex;
  flex-direction: row; 
  justify-content: center;
  align-items: center;
}
#actionBar {
  justify-content: center;
  align-items: center;
  margin-top: 0px;
  margin-left: 40%;
}
</style>
