<template>
  <div id="app">
    <div>검은마법사 패턴 타이머</div>
    <button @click="phaseSelect(1)"></button>
    <div id="phase1">
      <div @click="updateTrigger(0)">
        <Timer
          :time-left="timeLeft(0)"
          :timeLimit=timeLimit[0]
        />
      </div>
      <div @click="updateTrigger(1)">
        <Timer
          :time-left="timeLeft(1)"
          :timeLimit=timeLimit[1]
        />
      </div>
      <div @click="updateTrigger(2)">
        <Timer
          :time-left="timeLeft(2)"
          :timeLimit=timeLimit[2]
        />
      </div>
      <div @click="updateTrigger(3)">
        <Timer
          :time-left="timeLeft(3)"
          :timeLimit=timeLimit[3]
        />
      </div>
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
      phase: 1,
      timeLimit: [55, 55, 70, 35],
      timeTrigger: [0, 0, 0, 0],
      timePassed: 0,
      timerInterval: null,
      toggle: [0, 0, 0, 0]
    }
  },

  computed: {    
    
  },

  methods: {
    phaseSelect(n) {
      this.phase = n
    },

    startTimer() {
      this.timerInterval = setInterval(() => (this.timePassed += 1), 1000);
    },

    timeLeft(n) {
      if (this.toggle[n] == 0) {
        return this.timeLimit[n]
      }
      return this.timeLimit[n] - this.timePassed + this.timeTrigger[n]
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
