<template>
  <div id="app">
    <!-- tabindex="-1" @keyup.enter="phaseSelect(1)" -->
    <h1>검은마법사 패턴 타이머</h1>
    <br>
    <button @click="phaseSelect(1)">1페</button>
    <button @click="phaseSelect(2)">2페</button>
    <button @click="phaseSelect(3)">3페</button>
    <button @click="phaseSelect(4)">4페</button>
    <br>
    <br>
    <div id="phase1" v-if="phase == 1">
      <div @click="updateTrigger(0)">
        <div>
          <img class="pattern" src="src\assets\감자.gif" alt="potato">
        </div>
        <div class="label">
          <label>감자</label>
        </div>
        <Timer
          :time-left="timeLeft(0)"
          :timeLimit=timeLimit[0]
        />
      </div>
      <div @click="updateTrigger(1)">
        <div>
          <img class="pattern" src="src\assets\감자.gif" alt="potato">
        </div>
        <div class="label">
          <label>감자</label>
        </div>
        <Timer
          :time-left="timeLeft(1)"
          :timeLimit=timeLimit[1]
        />
      </div>
      <div @click="updateTrigger(2)">
        <div>
          <img class="pattern" src="src\assets\1페 권능.gif" alt="potato">
        </div>
        <div class="label">
          <label>권능</label>
        </div>
        <Timer
          :time-left="timeLeft(2)"
          :timeLimit=timeLimit[2]
        />
      </div>
    </div>
    <div id="phase2" v-if="phase == 2">
      <div @click="updateTrigger(3)">
        <div>
          <img class="pattern" src="src\assets\감자.gif" alt="potato">
        </div>
        <div class="label">
          <label>감자</label>
        </div>
        <Timer
          :time-left="timeLeft(3)"
          :timeLimit=timeLimit[3]
        />
      </div>
      <div @click="updateTrigger(4)">
        <div>
          <img class="pattern" src="src\assets\사선.gif" alt="potato">
        </div>
        <div class="label">
          <label>사선</label>
        </div>
        <Timer
          :time-left="timeLeft(4)"
          :timeLimit=timeLimit[4]
        />
      </div>
      <div @click="updateTrigger(5)">
        <div>
          <img class="pattern" src="src\assets\2페 권능.gif" alt="potato">
        </div>
        <div class="label">
          <label>권능</label>
        </div>
        <Timer
          :time-left="timeLeft(5)"
          :timeLimit=timeLimit[5]
        />
      </div>
      <div @click="updateTrigger(6)">
        <div>
          <img class="pattern" src="src\assets\눈.gif" alt="potato">
        </div>
        <div class="label">
          <label>눈</label>
        </div>
        <Timer
          :time-left="timeLeft(6)"
          :timeLimit=timeLimit[6]
        />
      </div>
    </div>
    <div id="phase3" v-if="phase == 3">
      <div @click="updateTrigger(7)">
        <div>
          <img class="pattern" src="src\assets\감자.gif" alt="potato">
        </div>
        <div class="label">
          <label>감자</label>
        </div>
        <Timer
          :time-left="timeLeft(7)"
          :timeLimit=timeLimit[7]
        />
      </div>
      <div @click="updateTrigger(8)">
        <div>
          <img class="pattern" src="src\assets\사선.gif" alt="potato">
        </div>
        <div class="label">
          <label>사선</label>
        </div>
        <Timer
          :time-left="timeLeft(8)"
          :timeLimit=timeLimit[8]
        />
      </div>
      <div @click="updateTrigger(9)">
        <div>
          <img class="pattern" src="src\assets\창조.gif" alt="potato">
        </div>
        <div class="label">
          <label>권능</label>
        </div>
        <Timer
          :time-left="timeLeft(9)"
          :timeLimit=timeLimit[9]
        />
      </div>
    </div>
    <div id="phase4" v-if="phase == 4">
      <div @click="updateTrigger(10)">
        <div>
          <img class="pattern" src="src\assets\4페 권능.gif" alt="potato">
        </div>
        <div class="label">
          <label>권능</label>
        </div>
        <Timer
          :time-left="timeLeft(10)"
          :timeLimit=timeLimit[10]
        />
      </div>
    </div>
    <br>
    <div id="nuking">
      <div @click="updateTrigger(11)">
        <Timer
          :time-left="timeLeft(11)"
          :timeLimit=timeLimit[11]
        />
      </div>
      <div @click="updateTrigger(12)">
        <Timer
          :time-left="timeLeft(12)"
          :timeLimit=timeLimit[12]
        />
      </div>
    </div>
  </div>
</template>

<script>
import Timer from './components/Timer.vue'


export default {
  name: 'App',

  components: {
    Timer,

  },
  
  created() {
    window.addEventListener('keypress', this.onKeyPress);
  },

  beforeDestroy() {
    window.removeEventListener('keypress', this.onKeyPress);
  },

  mounted() {
    this.startTimer();
  },

  data() {
    return {
      phase: 1,
      timeLimit: [20, 60, 40, 55, 55, 70, 35, 35, 35, 65, 30, 180, 120],
      timeTrigger: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      timePassed: 0,
      timerInterval: null,
      // toggle: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    }
  },

  computed: {    
    
  },

  methods: {
    onKeyPress(e) {
      if (e.key == '1')
        this.phaseSelect(1)
      if (e.key == '2')
        this.phaseSelect(2)
      if (e.key == '3')
        this.phaseSelect(3)
      if (e.key == '4')
        this.phaseSelect(4)
      if (e.key == 'd')
        this.updateTrigger(11)
      if (e.key == 'f')
        this.updateTrigger(12)
      if (this.phase == '1') {
        if (e.key == 'q') {
          this.updateTrigger(0)
        }
        if (e.key == 'w') {
          this.updateTrigger(1)
        }
        if (e.key == 'e') {
          this.updateTrigger(2)
        }
      }
      if (this.phase == '2') {
        if (e.key == 'q') {
          this.updateTrigger(3)
        }
        if (e.key == 'w') {
          this.updateTrigger(4)
        }
        if (e.key == 'e') {
          this.updateTrigger(5)
        }
        if (e.key == 'r') {
          this.updateTrigger(6)
        }
      }
      if (this.phase == '3') {
        if (e.key == 'q') {
          this.updateTrigger(7)
        }
        if (e.key == 'w') {
          this.updateTrigger(8)
        }
        if (e.key == 'e') {
          this.updateTrigger(9)
        }
      }
      if (this.phase == '4') {
        if (e.key == 'q') {
          this.updateTrigger(10)
        }
      }
    },
    
    phaseSelect(n) {
      this.phase = n
      if (n == 1) {
        this.timeTrigger[0] = this.timePassed
        this.timeTrigger[1] = this.timePassed
        this.timeTrigger[2] = this.timePassed
      }

      if (n == 2) {
        this.timeTrigger[3] = this.timePassed
        this.timeTrigger[4] = this.timePassed
        this.timeTrigger[5] = this.timePassed
        this.timeTrigger[6] = this.timePassed
      }

      if (n == 3) {
        this.timeTrigger[7] = this.timePassed
        this.timeTrigger[8] = this.timePassed
        this.timeTrigger[9] = this.timePassed
      }

      if (n == 4) {
        this.timeTrigger[10] = this.timePassed
      }
      
    },

    startTimer() {
      this.timerInterval = setInterval(() => (this.timePassed += 1), 1000);
    },

    timeLeft(n) {
      // if (this.toggle[n] == 0) {
      //   return this.timeLimit[n]
      // }
      return this.timeLimit[n] - this.timePassed + this.timeTrigger[n]
    },

    updateTrigger(n) {
      // this.toggle[n] = this.toggle[n] + 1
      this.timeTrigger[n] = this.timePassed
    },

  }
}
</script>
<style>
  div {
    display: block;
    float: left;
  }

  .pattern {
    width: 200px;
    height: 200px;
  }

  .label {
    padding: 100px 0;
  }

  button {
    width: 100px;
    height: 60px;
  }
</style>