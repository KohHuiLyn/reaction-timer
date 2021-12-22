<template>
  <p>Reaction time: {{score}} ms</p>
  <p class="rank">You are {{rank}}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank : null
        }
    },
    mounted(){
        if (this.score < 200){
            this.rank = "FAST AS HELL"
        } else if (this.score < 300) {
            this.rank = "Average..."
        } else {
            this.rank = "Slow as hell"
        }
    }
}
</script>

<style>
    .rank{
        font-size: 1.4em;
        font-weight: bold;
    }
</style>