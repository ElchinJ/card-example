<template>
  <section> 
    <Score id="score"/>
    <div id="app">
      <Card id="card" :card="{value, suite}"/>
      <Deck id="deck" :cards="topFive" faceDown/> 
    </div>
    <hr>
    <ActionBar id="actionBar" @guessCard='guessCardValue($event)' />
    <!-- <ActionBar id="actionBar" v-else-if @guessSame='guessSame'/>
    <ActionBar id="actionBar" v-else @guessLower='guessLower'/> -->
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
    value: 7,
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
    guessCardValue(guess) {
      const next = this.deck[0]
      if (guess == 'lower') {
        if(next.value < this.value){
        alert('Yes! Its lower');
      }else alert('Sorry! Wrong')
      }
      else if (guess == 'same') {
        if (next.value == this.value) {
        alert('Yes! Its equal');
      }else alert('Sorry! Wrong')
      }
      else if (guess == 'higher') {
        if (next.value > this.value) {
        alert('Yes! Its higher');
      }else alert('Sorry! Wrong')
      }
    },
    // guessSame(){
    //   let nextCard = this.deck[0]
    //   if(nextCard.value == this.value){
    //     alert('Du gissade rätt!!!');
    //   }
    // },
    // guessHigher() {
    //   let nextCard = this.deck[0]
    //   if(nextCard.value > this.value){
    //     alert('Du gissade rätt!!!');
    //   }
    // }
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
