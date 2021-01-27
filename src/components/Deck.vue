<template>
  <article class="deck">
    <Card v-for="(card,index) in cards" :key="card.suite+card.value" :card="card" :style="`z-index: ${index}`"/>
  </article>
</template>

<script>
import Card from '@/components/Card'
export default {
    components: {Card},
  props: {
    cards: Array
  }

}
</script>

<style>

.deck{
  display: grid;
  grid-auto-rows: 10px;
}

</style>