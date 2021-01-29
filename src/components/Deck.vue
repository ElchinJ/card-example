<template>
  <article class="deck">
      <Card v-for="(card,index) in cards.slice().reverse()" :key="card.suite+card.value" :card="card" :style="`z-index: ${index}`" :faceDown="faceDown"/>
  </article>
</template>

<script>
import Card from '@/components/Card'

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
.deck {
  &.face-down{
    background-color: hotpink;
    background-image: url('~@/assets/dots.svg');
    margin-left: 1rem;
  }
}

</style>