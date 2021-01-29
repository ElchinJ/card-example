<template>
    <div>
        <label>Attempts: {{scoreProps.attempts}}</label><br>
        <label>Points: {{scoreProps.points}}</label><br>
        <label>Cards left: {{scoreProps.heap}}</label>
    </div>
</template>

<script>
    export default {
        name: 'Score',
        props: ['scoreProps'],
    }
    
</script>

<style lang="scss" scoped>

label {
    color: white;
    font-weight: bold;
    list-style-type:none;
    margin: 0;
    padding: 0;
}

</style>