<template>
    <div>
        <p>Reaction time: {{ score }} ms</p>
        <p class="rank"> {{ rank }}</p>
    </div>
   
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },

    mounted() {
        if (this.score < 250) {
            this.rank = 'super speedy'
        } else if (this.score < 400) {
            this.rank = "speedy"
        } else {
            this.rank = "not speedy..."
        }
    }
}
</script>

<style>
    .rank{
        font-size: 1.4em;
        color:lightblue;
        font-weight: bold;
    }
</style>