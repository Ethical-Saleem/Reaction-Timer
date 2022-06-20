<template>
  <p id="score"> Your Reaction Time is: {{ score }}</p>
  <p class="rank"> {{ rank }}</p>
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
    if (this.score < 180) {
        this.rank = 'Ninja Master (Hokage)'
    } else if (this.score < 300) {
        this.rank = 'Ninja Fingers (Jonin)'
    } else if (this.score < 400) {
        this.rank = 'Rapid Reflexes (Chunin)'
    } else if (this.score < 500) {
        this.rank = 'Slow Fingers (Genin)'
    } else  {
        this.rank = 'Snail Pace...'
    }
  }
}
</script>

<style>
  .rank {
    font-size: 1.4em;
    color: rgba(5, 2, 24, 0.849);
    font-weight: bold;
  }
  #score {
    color: rgba(39, 11, 223, 0.8);
    font-weight: bold;
  }
</style>