<template>
  <div id="app" class="outer">
    <h2>검은 마법사 패턴 타이머</h2>
    <span>제작자 : 루나/아르마멍</span>
    <br>
    <span>사용설명 : <a href="https://www.inven.co.kr/board/maple/2304/32341">링크 클릭</a></span>
    <br>
    <span>버그/오류제보 : <a href="https://open.kakao.com/me/dgdg">링크 클릭</a></span>
    <br>
    <button @click="phaseSelect(1)">1페 (1)</button>
    <button @click="phaseSelect(2)">2페 (2)</button>
    <button @click="phaseSelect(3)">3페 (3)</button>
    <button @click="phaseSelect(4)">4페 (4)</button>
    <br>
    <div id="phase1" v-if="phase == 1">
      <div @click="updateTrigger(0)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/potato.gif" alt="potato">
          <span class="caption">감자 (Q)</span>
        </div>
        <div class="timer">
          <Timer
          :time-left="timeLeft(0)"
          :timeLimit=timeLimit[0]
        />
        </div>
      </div>
      <div @click="updateTrigger(1)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/lightning.gif" alt="lightning">
          <span class="caption">전기 (W)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(1)"
            :timeLimit=timeLimit[1]
          />
        </div>
      </div>
      <div @click="updateTrigger(2)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/gim1.gif" alt="gim1">
          <span class="caption">권능 (E)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(2)"
            :timeLimit=timeLimit[2]
          />
        </div>
      </div>
    </div>
    <div id="phase2" v-if="phase == 2">
      <div @click="updateTrigger(3)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/potato.gif" alt="potato">
          <span class="caption">감자 (Q)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(3)"
            :timeLimit=timeLimit[3]
          />
        </div>
      </div>
      <div @click="updateTrigger(4)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/dog.gif" alt="dog">
          <span class="caption">사선 (W)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(4)"
            :timeLimit=timeLimit[4]
          />
        </div>
      </div>
      <div @click="updateTrigger(5)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/gim2.gif" alt="gim2">
          <span class="caption">권능 (E)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(5)"
            :timeLimit=timeLimit[5]
          />
        </div>
      </div>
      <div @click="updateTrigger(6)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/eye.gif" alt="eye">
          <span class="caption">눈 (R)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(6)"
            :timeLimit=timeLimit[6]
          />
        </div>
      </div>
    </div>
    <div id="phase3" v-if="phase == 3">
      <div @click="updateTrigger(7)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/potato.gif" alt="potato">
          <span class="caption">감자 (Q)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(7)"
            :timeLimit=timeLimit[7]
          />
        </div>
      </div>
      <div @click="updateTrigger(8)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/dog.gif" alt="dog">
          <span class="caption">사선 (W)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(8)"
            :timeLimit=timeLimit[8]
          />
        </div>
      </div>
      <div @click="updateTrigger(9)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/gim3.gif" alt="gim3">
          <span class="caption">권능 (E)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(9)"
            :timeLimit=timeLimit[9]
          />
        </div>
      </div>
    </div>
    <div id="phase4" v-if="phase == 4">
      <div @click="updateTrigger(10)" class="cont">
        <div class="imgcap">
          <img class="pattern" src="./assets/gim4.gif" alt="gim4">
          <span class="caption">권능 (Q)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(10)"
            :timeLimit=timeLimit[10]
          />
        </div>
      </div>
    </div>
    <br>
    <div id="nuking">
      <div @click="updateTrigger(11)" class="cont">
        <div class="imgcap">
          <img class="nuke" src="./assets/180.png" alt="180">
          <span class="caption">3분 극딜 (D)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(11)"
            :timeLimit=timeLimit[11]
          />
        </div>
      </div>
      <div @click="updateTrigger(12)" class="cont">
        <div class="imgcap">
          <img class="nuke" src="./assets/120.png" alt="120">
          <span class="caption">2분 극딜 (F)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(12)"
            :timeLimit=timeLimit[12]
          />
        </div>
      </div>
      <div @click="updateTrigger(13)" class="cont">
        <div class="imgcap">
          <img class="nuke" src="./assets/200.png" alt="200">
          <span class="caption">200초 (G)</span>
        </div>
        <div class="timer">
          <Timer
            :time-left="timeLeft(13)"
            :timeLimit=timeLimit[13]
          />
        </div>
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
      timeLimit: [20, 60, 40, 55, 55, 70, 35, 35, 35, 65, 30, 180, 120, 200],
      timeTrigger: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      timePassed: 0,
      timerInterval: null,
      // toggle: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
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
      if (e.key == 'd' || e.key == 'D')
        this.updateTrigger(11)
      if (e.key == 'f' || e.key == 'F')
        this.updateTrigger(12)
      if (e.key == 'g' || e.key == 'G')
        this.updateTrigger(13)
      if (this.phase == '1') {
        if (e.key == 'q' || e.key == 'Q') {
          this.updateTrigger(0)
        }
        if (e.key == 'w' || e.key == 'W') {
          this.updateTrigger(1)
        }
        if (e.key == 'e' || e.key == 'E') {
          this.updateTrigger(2)
        }
      }
      if (this.phase == '2') {
        if (e.key == 'q' || e.key == 'Q') {
          this.updateTrigger(3)
        }
        if (e.key == 'w' || e.key == 'W') {
          this.updateTrigger(4)
        }
        if (e.key == 'e' || e.key == 'E') {
          this.updateTrigger(5)
        }
        if (e.key == 'r' || e.key == 'R') {
          this.updateTrigger(6)
        }
      }
      if (this.phase == '3') {
        if (e.key == 'q' || e.key == 'Q') {
          this.updateTrigger(7)
        }
        if (e.key == 'w' || e.key == 'W') {
          this.updateTrigger(8)
        }
        if (e.key == 'e' || e.key == 'E') {
          this.updateTrigger(9)
        }
      }
      if (this.phase == '4') {
        if (e.key == 'q' || e.key == 'Q') {
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
      return this.timeLimit[n] - this.timePassed + this.timeTrigger[n]
    },

    updateTrigger(n) {
      this.timeTrigger[n] = this.timePassed
    },

  }
}
</script>
<style>
  @font-face {
    font-family: 'NexonMaplestory';
    font-weight: 300;
    font-style: normal;
    src: url('https://cdn.jsdelivr.net/gh/webfontworld/NexonMaplestory/NexonMaplestoryLight.eot');
    src: url('https://cdn.jsdelivr.net/gh/webfontworld/NexonMaplestory/NexonMaplestoryLight.eot?#iefix') format('embedded-opentype'),
         url('https://cdn.jsdelivr.net/gh/webfontworld/NexonMaplestory/NexonMaplestoryLight.woff2') format('woff2'),
         url('https://cdn.jsdelivr.net/gh/webfontworld/NexonMaplestory/NexonMaplestoryLight.woff') format('woff'),
         url('https://cdn.jsdelivr.net/gh/webfontworld/NexonMaplestory/NexonMaplestoryLight.ttf') format("truetype");
    font-display: swap;
  }

  div {
    display: block;
    float: left;
    font-family: 'NexonMaplestory';
  }

  .cont {
    width: 120px;
    height: 90px;
  }

  .imgcap {
    width: 60px;
    height: 90px;
  }

  .pattern {
    width: 60px;
    height: 60px;
  }

  .nuke {
    width: 32px;
    height: 32px;
    margin: 14px;
  }

  button {
    width: 70px;
    height: 40px;
    margin: 5px;
    border-style: solid;
    border-color: black;
    font-size: 12px;
  }

  .outer {
    border-style: solid;
    border-color: black;
    border-radius: 10px;
    background-color: white;
    text-align: center;
    color: black;
  }

  div.item {
    vertical-align: top;
    display: inline-block;
    text-align: center;
    width: 120px;
  }

  .caption {
    display: block;
    font-size: 10px;
    position: relative;
    bottom: 15px;
  }

  .timer {
    position: relative;
    top: 5px;
  }

</style>