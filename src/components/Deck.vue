<template>
  <article class="deck">
      <Card v-for="(card,index) in cards" :key="card.suite+card.value" :card="card" :style="`z-index: ${index}`"/>
  </article>
</template>

<script>
import Card from '@/components/Card'

Array.prototype.shuffle = function(){
  return this.sort(() => Math.random()-0.5 )
}

export default {
    components: {Card},
    props: {
      cards: Array,
      faceDown: Boolean,
  }
}
</script>

<style lang="scss" scoped>

.deck{
  display: grid;
  grid-auto-rows: 10px;
  margin-bottom: 370px;
  margin-left: 10px;
}

</style>