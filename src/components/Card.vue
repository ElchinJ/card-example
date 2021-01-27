<template>
  <article >
    <div v-if="!faceDown" class="card">
      <span class="top">
        <img :src="icon" class="icon">
        <p>{{displayValue}}</p>
      </span>

      <img :src="icon" class="icon large">
      
      <span class="bottom">
        <img :src="icon" class="icon">
        <p>{{displayValue}}</p>
      </span>

    </div>
    <div v-else class="card face-down"></div>
  </article>
</template>

<script>

export default {
  props: {
    card: Object,
    faceDown: Boolean,
  },
  computed: {
    icon(){
      return require(`@/assets/${this.card.suite.toLowerCase()}.svg`)
    },
    displayValue(){
      switch(this.card.value){
        case 14:
        case 1: return 'A';
        case 11: return 'J';
        case 12: return 'Q';
        case 13: return 'K';
        default: return this.card.value
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.card{
  width: 18rem;
  height: 26rem;
  background-color: #EEE;
  border-radius: 12px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  border: 10px solid white;
  padding: 1rem;
  box-sizing: border-box;
  box-shadow: 0px -1px 1px 1px rgba(0,0,0,0.27);

  p{
    margin:0; padding: 0;
    font-weight: 900;
    font-size: 1.5rem;
  }

  .top{ 
    align-self: flex-start;
    p {
          font-size: 3rem;
    }
    }
  .bottom{ 
    align-self: flex-end;
     p {
          font-size: 3rem;
    }}
  .bottom{
    transform: rotate(180deg)
  }

  &.face-down{
    background-color: hotpink;
    background-image: url('~@/assets/dots.svg');
    margin-left: 1rem;
  }
}

.icon{
  width: 2rem;
  height: 2rem;

  &.large{
    width: 6rem;
    height: 6rem;
  }
}
</style>