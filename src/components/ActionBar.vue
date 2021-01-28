<template>
  <div id="buttons">
    <button @click="turnCard">Lower</button>
    <button @click="turnCard">Equal</button>
    <button @click="turnCard">Higher</button>
  </div>
</template>

<script>
export default {
    name: 'ActionBar',
    methods: {
      turnCard(){
        this.$emit('turn')
    }
  }
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