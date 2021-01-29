<template>
  <section> 
    <Score id="score" :scoreProps="scores"/>
    <div id="app">
      <Card id="card" :card="headCard"/>
      <Deck id="deck" :cards="topFive.reverse()" :faceDown="faceDown"/> 
    </div>
    <hr>
    <ActionBar id="actionBar" @guessCard='guessCardValue($event)' />
  </section>
</template>

<script>
import Card from '@/components/Card'
import Deck from '@/components/Deck'
import Score from '@/components/Score'
import ActionBar from '@/components/ActionBar'

Array.prototype.shuffle = function(){
  return this.sort(() => Math.random()-0.5 )
}

export default {
  name: 'App',
  components: {Card, Deck, Score, ActionBar},

  data(){ return {
    deck: [],
    suites: ["Hearts", "Spades", "Diamonds", "Clubs"],
    scores: {
      attempts: 0,
      points: 0,
      heap: 51
    },
    faceDown: Boolean,
  }},

  computed: {
    topFive(){
      return this.deck.filter((_,i) => i < 5)
    },
    headCard: function() {
      let value = Math.floor(Math.random() * Math.floor(14))
      let suite = this.suites[Math.floor(Math.random() * this.suites.length)]; 
      return {value, suite}
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
  methods: {
    guessCardValue(guess) {
      this.scores.attempts++
      const nextCard = this.topFive[0]
      this.faceDown = false

      if (guess == 'lower') {
        if(nextCard.value < this.headCard.value){
        this.scores.points++
        alert('Yes! Its lower');
      }else alert('Sorry! Wrong')
      }
      else if (guess == 'same') {
        if (nextCard.value == this.headCard.value) {
          this.scores.points++
        alert('Yes! Its equal');
      }else alert('Sorry! Wrong')
      }
      else if (guess == 'higher') {
        if (nextCard.value > this.headCard.value) {
          this.scores.points++
        alert('Yes! Its higher');
      }else alert('Sorry! Wrong')
      }
      this.scores.heap--
    },
},
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
