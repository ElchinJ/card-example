<template>
  <div id="buttons">
    <button @click="guessCard('lower')">Lower</button>
    <button @click="guessCard('same')">Equal</button>
    <button @click="guessCard('higher')">Higher</button>
  </div>
</template>

<script>
export default {
    name: 'ActionBar',
    methods: {
      guessCard(btn) {
        if (btn == 'lower') {
          this.$emit('guessCard', 'lower')
        }else if (btn == 'same') {
          this.$emit('guessCard', 'same')
        } else {
          this.$emit('guessCard', 'higher')
        }
      }
    },
  //   methods: {
  //     guessLower(){
  //       this.$emit('guessLower')
  //   },
  //   guessSame() {
  //     this.$emit('guessSame')
  //   },
  //   guessHigher() {
  //     this.$emit('guessHigher')
  //   }
  // }
}
</script>

<style>
#buttons {
  justify-content: center;
  align-items: center;
}
button {
  background-color: black;
  color: white;
  border-radius: 45px;
  width: 6rem;
  height: 2rem;
}
button:focus{
    background:white;
    color: black;
    font-weight: bold;
}

</style>