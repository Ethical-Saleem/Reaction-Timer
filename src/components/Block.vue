<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click Me
  </div>
</template>

<script>
export default {
props: ['delay'],
data() {
    return {
        showBlock: false,
        timer: null,
        reactTime: 0
    }
},
mounted() {
    console.log('component mounted')
      setTimeout(() => {
        this.showBlock = true
        this.startTimer()
        console.log(this.delay)
      }, this.delay)
    },
methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      console.log(this.reactTime)
      this.$emit('end', this.reactTime)
    }
}
}
</script>

<style>
  .block {
    width: 400px;
    border-radius: 25px;
    background: rgba(5, 2, 24, 0.849);
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>