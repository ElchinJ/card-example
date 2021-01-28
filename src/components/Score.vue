<template>
    <div>
        <span>
            <label>Attempts left: </label>
            <label>{{attempts}}</label>
        </span>
        <span>
            <label>Points: </label>
            <label>{{points}}</label>
        </span>
        <span>
            <label>Cards left: </label>
            <label>{{heap}}</label>
        </span>
    </div>
</template>

<script>
    export default {
        name: 'Score',
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
hr {
    visibility: hidden;
}
label {
    color: white;
    font-weight: bold;
}
div {
    display: flex;
    flex-direction: column;
}
</style>