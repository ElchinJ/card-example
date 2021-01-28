<template>
  <div id="buttons">
    <button>Lower</button>
    <button>Equal</button>
    <button>Higher</button>
  </div>
</template>

<script>
export default {
    name: 'ActionBar',
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