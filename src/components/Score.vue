<template>
    <div>
        <label>Attempts left: </label>
        <p>{{attempts}}</p>
        <label>Points: </label>
        <p>{{points}}</p>
        <label>Cards left: </label>
        <p>{{heap}}</p>
    </div>
</template>

<script>
    export default {
        name: Score,
        data() {
            return {
                attempts: 0,
                points: 0,
                heap: 0,
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>