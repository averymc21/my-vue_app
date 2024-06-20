<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
  props: ['delay'],

  data () {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    // this function stores time data and run every 10 milisecs, and add 10 milisecs to reaction time
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      //console.log(this.reactionTime)
      this.$emit('end', this.reactionTime)
    }
  }

}
</script>

<style>
    .block {
        width:400px;
        border-radius: 20px;
        background: lightblue; 
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>