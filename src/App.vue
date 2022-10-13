<template>
  <div id="app">
    <div @click="updateTrigger(0)">
      <Timer
        :time-left="timeLeft0"
        :timeLimit=timeLimit[0]
      />
    </div>
    <div @click="updateTrigger(1)">
      <Timer
        :time-left="timeLeft1"
        :timeLimit=timeLimit[1]
      />
    </div>
    <button @click="log"></button>
  </div>
</template>

<script>
import Timer from './components/Timer.vue'

export default {
  name: 'App',

  components: {
    Timer
  },
  
  mounted() {
    this.startTimer();
  },

  data() {
    return {
      timeLimit: [20, 30],
      timeTrigger: [0, 0],
      timePassed: 0,
      timerInterval: null,
      toggle: [0, 0]
    }
  },

  computed: {
    timeLeft0() {
      if (this.toggle[0] = 0) {
        return this.timeLimit[0]
      }
      return this.timeLimit[0] - this.timePassed + this.timeTrigger[0]
    },

    timeLeft1() {
      return this.timeLimit[1] - this.timePassed + this.timeTrigger[1]
    },
    
  },

  methods: {
    startTimer() {
      this.timerInterval = setInterval(() => (this.timePassed += 1), 1000);
    },

    updateTrigger(n) {
      this.toggle[n] = this.toggle[n] + 1
      this.timeTrigger[n] = this.timePassed
    },

    log() {
      console.log(this.timeTrigger)
      console.log(this.timeLimit)
      console.log(this.timePassed)
      console.log(this.toggle)
    }
  }
}
</script>
