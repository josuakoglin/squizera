<script setup lang="ts">
import { ref, onMounted } from 'vue'

const showModal = ref<boolean>(false)
const isLoading = ref<boolean>(true)
const loadingTextIndex = ref<number>(0)

const loadingTexts = [
  "Loading Switzerland…",
  "Don't worry, won't take long…",
  "Only 9,051,029 residents remaining",
  "Counting chocolate factories…",
  "Syncing with Alps…",
  "Calibrating cheese holes…",
  "Polishing watches…",
  "Yodeling initialization…",
  "Banking your data securely…",
  "Neutralizing information…",
  "Optimizing Swiss precision…",
  "Verifying neutrality protocols…",
  "Almost there…",
  "Final fondue check…"
]

const openModal = (): void => {
  showModal.value = true
}

const closeModal = (): void => {
  showModal.value = false
}

onMounted(() => {
  const textChangeInterval = 2500
  const totalDuration = loadingTexts.length * textChangeInterval

  const textInterval = setInterval(() => {
    if (loadingTextIndex.value < loadingTexts.length - 1) {
      loadingTextIndex.value++
    }
  }, textChangeInterval)

  setTimeout(() => {
    clearInterval(textInterval)
    isLoading.value = false
  }, totalDuration)
})
</script>

<template>
  <div class="background">
    <div class="sky"></div>
    <div class="snowfall">
      <div class="snow" v-for="n in 200" :key="n"></div>
    </div>

    <div class="card">
      <h1 class="title">sQUIZera</h1>
      <div class="button-container">
        <Transition name="fade-button" mode="out-in">
          <button v-if="!isLoading" key="button" class="loading-button" @click="openModal">
            <span class="button-text">Tap to Suizify</span>
          </button>
          <div v-else key="loading" class="loading-bar">
            <div class="loading-bar-fill"></div>
            <span class="loading-text">{{ loadingTexts[loadingTextIndex] }}</span>
          </div>
        </Transition>
      </div>
    </div>

    <Transition name="fade">
      <div v-if="showModal" class="modal-overlay" @click="closeModal">
        <div class="modal" @click.stop>
          <p class="modal-text">
            Oops… this feature only unlocks after a real-life Switzerland visit.
          </p>
          <p class="modal-subtext">
            Come to Switzerland. The game will know.
          </p>
          <button class="modal-button" @click="closeModal">
            Got it
          </button>
        </div>
      </div>
    </Transition>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Fredoka+One&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  overflow: hidden;
  padding: 1rem;
}

.sky {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('./sQUIZera.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  z-index: 0;
}

.snowfall {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  pointer-events: none;
  overflow: hidden;
}

.snow {
  position: absolute;
  top: -10px;
  width: 10px;
  height: 10px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.9) 0%, rgba(255, 255, 255, 0.3) 60%, transparent 70%);
  border-radius: 50%;
  animation: snowfall linear infinite;
}

.snow:nth-child(1) { left: 5%; animation-duration: 8s; animation-delay: 0s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(2) { left: 10%; animation-duration: 12s; animation-delay: 1s; width: 6px; height: 6px; opacity: 0.6; }
.snow:nth-child(3) { left: 15%; animation-duration: 10s; animation-delay: 0.5s; width: 12px; height: 12px; opacity: 0.9; }
.snow:nth-child(4) { left: 20%; animation-duration: 14s; animation-delay: 2s; width: 5px; height: 5px; opacity: 0.5; }
.snow:nth-child(5) { left: 25%; animation-duration: 9s; animation-delay: 1.5s; width: 10px; height: 10px; opacity: 0.7; }
.snow:nth-child(6) { left: 30%; animation-duration: 11s; animation-delay: 0s; width: 7px; height: 7px; opacity: 0.8; }
.snow:nth-child(7) { left: 35%; animation-duration: 13s; animation-delay: 3s; width: 9px; height: 9px; opacity: 0.6; }
.snow:nth-child(8) { left: 40%; animation-duration: 8s; animation-delay: 2.5s; width: 11px; height: 11px; opacity: 0.9; }
.snow:nth-child(9) { left: 45%; animation-duration: 15s; animation-delay: 1s; width: 6px; height: 6px; opacity: 0.5; }
.snow:nth-child(10) { left: 50%; animation-duration: 10s; animation-delay: 0s; width: 8px; height: 8px; opacity: 0.7; }
.snow:nth-child(11) { left: 55%; animation-duration: 12s; animation-delay: 4s; width: 10px; height: 10px; opacity: 0.8; }
.snow:nth-child(12) { left: 60%; animation-duration: 9s; animation-delay: 1.5s; width: 7px; height: 7px; opacity: 0.6; }
.snow:nth-child(13) { left: 65%; animation-duration: 14s; animation-delay: 2s; width: 12px; height: 12px; opacity: 0.9; }
.snow:nth-child(14) { left: 70%; animation-duration: 11s; animation-delay: 0.5s; width: 5px; height: 5px; opacity: 0.5; }
.snow:nth-child(15) { left: 75%; animation-duration: 8s; animation-delay: 3.5s; width: 9px; height: 9px; opacity: 0.7; }
.snow:nth-child(16) { left: 80%; animation-duration: 13s; animation-delay: 1s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(17) { left: 85%; animation-duration: 10s; animation-delay: 0s; width: 11px; height: 11px; opacity: 0.6; }
.snow:nth-child(18) { left: 90%; animation-duration: 15s; animation-delay: 2.5s; width: 6px; height: 6px; opacity: 0.9; }
.snow:nth-child(19) { left: 95%; animation-duration: 9s; animation-delay: 4s; width: 10px; height: 10px; opacity: 0.5; }
.snow:nth-child(20) { left: 3%; animation-duration: 12s; animation-delay: 1.5s; width: 7px; height: 7px; opacity: 0.7; }
.snow:nth-child(21) { left: 8%; animation-duration: 11s; animation-delay: 3s; width: 9px; height: 9px; opacity: 0.8; }
.snow:nth-child(22) { left: 13%; animation-duration: 14s; animation-delay: 0s; width: 5px; height: 5px; opacity: 0.6; }
.snow:nth-child(23) { left: 18%; animation-duration: 8s; animation-delay: 2s; width: 12px; height: 12px; opacity: 0.9; }
.snow:nth-child(24) { left: 23%; animation-duration: 10s; animation-delay: 4.5s; width: 8px; height: 8px; opacity: 0.5; }
.snow:nth-child(25) { left: 28%; animation-duration: 13s; animation-delay: 1s; width: 6px; height: 6px; opacity: 0.7; }
.snow:nth-child(26) { left: 33%; animation-duration: 9s; animation-delay: 0.5s; width: 10px; height: 10px; opacity: 0.8; }
.snow:nth-child(27) { left: 38%; animation-duration: 15s; animation-delay: 3.5s; width: 11px; height: 11px; opacity: 0.6; }
.snow:nth-child(28) { left: 43%; animation-duration: 11s; animation-delay: 2s; width: 7px; height: 7px; opacity: 0.9; }
.snow:nth-child(29) { left: 48%; animation-duration: 12s; animation-delay: 0s; width: 9px; height: 9px; opacity: 0.5; }
.snow:nth-child(30) { left: 53%; animation-duration: 8s; animation-delay: 1.5s; width: 5px; height: 5px; opacity: 0.7; }
.snow:nth-child(31) { left: 58%; animation-duration: 14s; animation-delay: 4s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(32) { left: 63%; animation-duration: 10s; animation-delay: 2.5s; width: 12px; height: 12px; opacity: 0.6; }
.snow:nth-child(33) { left: 68%; animation-duration: 9s; animation-delay: 0s; width: 6px; height: 6px; opacity: 0.9; }
.snow:nth-child(34) { left: 73%; animation-duration: 13s; animation-delay: 3s; width: 10px; height: 10px; opacity: 0.5; }
.snow:nth-child(35) { left: 78%; animation-duration: 11s; animation-delay: 1s; width: 7px; height: 7px; opacity: 0.7; }
.snow:nth-child(36) { left: 83%; animation-duration: 15s; animation-delay: 0.5s; width: 11px; height: 11px; opacity: 0.8; }
.snow:nth-child(37) { left: 88%; animation-duration: 8s; animation-delay: 2s; width: 9px; height: 9px; opacity: 0.6; }
.snow:nth-child(38) { left: 93%; animation-duration: 12s; animation-delay: 4.5s; width: 5px; height: 5px; opacity: 0.9; }
.snow:nth-child(39) { left: 98%; animation-duration: 10s; animation-delay: 1.5s; width: 8px; height: 8px; opacity: 0.5; }
.snow:nth-child(40) { left: 2%; animation-duration: 14s; animation-delay: 3.5s; width: 6px; height: 6px; opacity: 0.7; }
.snow:nth-child(41) { left: 12%; animation-duration: 9s; animation-delay: 0s; width: 10px; height: 10px; opacity: 0.8; }
.snow:nth-child(42) { left: 22%; animation-duration: 11s; animation-delay: 2.5s; width: 12px; height: 12px; opacity: 0.6; }
.snow:nth-child(43) { left: 32%; animation-duration: 13s; animation-delay: 1s; width: 7px; height: 7px; opacity: 0.9; }
.snow:nth-child(44) { left: 42%; animation-duration: 8s; animation-delay: 4s; width: 9px; height: 9px; opacity: 0.5; }
.snow:nth-child(45) { left: 52%; animation-duration: 15s; animation-delay: 0.5s; width: 11px; height: 11px; opacity: 0.7; }
.snow:nth-child(46) { left: 62%; animation-duration: 10s; animation-delay: 3s; width: 5px; height: 5px; opacity: 0.8; }
.snow:nth-child(47) { left: 72%; animation-duration: 12s; animation-delay: 2s; width: 8px; height: 8px; opacity: 0.6; }
.snow:nth-child(48) { left: 82%; animation-duration: 9s; animation-delay: 1.5s; width: 6px; height: 6px; opacity: 0.9; }
.snow:nth-child(49) { left: 92%; animation-duration: 14s; animation-delay: 0s; width: 10px; height: 10px; opacity: 0.5; }
.snow:nth-child(50) { left: 7%; animation-duration: 11s; animation-delay: 4.5s; width: 7px; height: 7px; opacity: 0.7; }
.snow:nth-child(51) { left: 4%; animation-duration: 9s; animation-delay: 5s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(52) { left: 11%; animation-duration: 13s; animation-delay: 0.5s; width: 6px; height: 6px; opacity: 0.6; }
.snow:nth-child(53) { left: 16%; animation-duration: 8s; animation-delay: 3s; width: 11px; height: 11px; opacity: 0.9; }
.snow:nth-child(54) { left: 21%; animation-duration: 12s; animation-delay: 1.5s; width: 5px; height: 5px; opacity: 0.5; }
.snow:nth-child(55) { left: 26%; animation-duration: 10s; animation-delay: 4s; width: 9px; height: 9px; opacity: 0.7; }
.snow:nth-child(56) { left: 31%; animation-duration: 15s; animation-delay: 2s; width: 7px; height: 7px; opacity: 0.8; }
.snow:nth-child(57) { left: 36%; animation-duration: 11s; animation-delay: 0s; width: 10px; height: 10px; opacity: 0.6; }
.snow:nth-child(58) { left: 41%; animation-duration: 9s; animation-delay: 5.5s; width: 12px; height: 12px; opacity: 0.9; }
.snow:nth-child(59) { left: 46%; animation-duration: 14s; animation-delay: 1s; width: 6px; height: 6px; opacity: 0.5; }
.snow:nth-child(60) { left: 51%; animation-duration: 8s; animation-delay: 3.5s; width: 8px; height: 8px; opacity: 0.7; }
.snow:nth-child(61) { left: 56%; animation-duration: 13s; animation-delay: 2.5s; width: 11px; height: 11px; opacity: 0.8; }
.snow:nth-child(62) { left: 61%; animation-duration: 10s; animation-delay: 0.5s; width: 7px; height: 7px; opacity: 0.6; }
.snow:nth-child(63) { left: 66%; animation-duration: 12s; animation-delay: 4.5s; width: 9px; height: 9px; opacity: 0.9; }
.snow:nth-child(64) { left: 71%; animation-duration: 9s; animation-delay: 1.5s; width: 5px; height: 5px; opacity: 0.5; }
.snow:nth-child(65) { left: 76%; animation-duration: 15s; animation-delay: 3s; width: 10px; height: 10px; opacity: 0.7; }
.snow:nth-child(66) { left: 81%; animation-duration: 11s; animation-delay: 0s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(67) { left: 86%; animation-duration: 8s; animation-delay: 5s; width: 12px; height: 12px; opacity: 0.6; }
.snow:nth-child(68) { left: 91%; animation-duration: 14s; animation-delay: 2s; width: 6px; height: 6px; opacity: 0.9; }
.snow:nth-child(69) { left: 96%; animation-duration: 10s; animation-delay: 4s; width: 11px; height: 11px; opacity: 0.5; }
.snow:nth-child(70) { left: 1%; animation-duration: 13s; animation-delay: 1s; width: 7px; height: 7px; opacity: 0.7; }
.snow:nth-child(71) { left: 9%; animation-duration: 9s; animation-delay: 3.5s; width: 9px; height: 9px; opacity: 0.8; }
.snow:nth-child(72) { left: 14%; animation-duration: 12s; animation-delay: 0.5s; width: 5px; height: 5px; opacity: 0.6; }
.snow:nth-child(73) { left: 19%; animation-duration: 15s; animation-delay: 5.5s; width: 10px; height: 10px; opacity: 0.9; }
.snow:nth-child(74) { left: 24%; animation-duration: 8s; animation-delay: 2.5s; width: 8px; height: 8px; opacity: 0.5; }
.snow:nth-child(75) { left: 29%; animation-duration: 11s; animation-delay: 0s; width: 6px; height: 6px; opacity: 0.7; }
.snow:nth-child(76) { left: 34%; animation-duration: 10s; animation-delay: 4.5s; width: 12px; height: 12px; opacity: 0.8; }
.snow:nth-child(77) { left: 39%; animation-duration: 14s; animation-delay: 1.5s; width: 11px; height: 11px; opacity: 0.6; }
.snow:nth-child(78) { left: 44%; animation-duration: 9s; animation-delay: 3s; width: 7px; height: 7px; opacity: 0.9; }
.snow:nth-child(79) { left: 49%; animation-duration: 13s; animation-delay: 5s; width: 9px; height: 9px; opacity: 0.5; }
.snow:nth-child(80) { left: 54%; animation-duration: 8s; animation-delay: 0.5s; width: 5px; height: 5px; opacity: 0.7; }
.snow:nth-child(81) { left: 59%; animation-duration: 12s; animation-delay: 2s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(82) { left: 64%; animation-duration: 15s; animation-delay: 4s; width: 10px; height: 10px; opacity: 0.6; }
.snow:nth-child(83) { left: 69%; animation-duration: 10s; animation-delay: 1s; width: 6px; height: 6px; opacity: 0.9; }
.snow:nth-child(84) { left: 74%; animation-duration: 11s; animation-delay: 5.5s; width: 12px; height: 12px; opacity: 0.5; }
.snow:nth-child(85) { left: 79%; animation-duration: 9s; animation-delay: 3.5s; width: 7px; height: 7px; opacity: 0.7; }
.snow:nth-child(86) { left: 84%; animation-duration: 14s; animation-delay: 0s; width: 11px; height: 11px; opacity: 0.8; }
.snow:nth-child(87) { left: 89%; animation-duration: 8s; animation-delay: 2.5s; width: 9px; height: 9px; opacity: 0.6; }
.snow:nth-child(88) { left: 94%; animation-duration: 13s; animation-delay: 4.5s; width: 5px; height: 5px; opacity: 0.9; }
.snow:nth-child(89) { left: 99%; animation-duration: 10s; animation-delay: 1.5s; width: 8px; height: 8px; opacity: 0.5; }
.snow:nth-child(90) { left: 6%; animation-duration: 12s; animation-delay: 3s; width: 10px; height: 10px; opacity: 0.7; }
.snow:nth-child(91) { left: 17%; animation-duration: 15s; animation-delay: 5s; width: 6px; height: 6px; opacity: 0.8; }
.snow:nth-child(92) { left: 27%; animation-duration: 9s; animation-delay: 0.5s; width: 12px; height: 12px; opacity: 0.6; }
.snow:nth-child(93) { left: 37%; animation-duration: 11s; animation-delay: 2s; width: 7px; height: 7px; opacity: 0.9; }
.snow:nth-child(94) { left: 47%; animation-duration: 8s; animation-delay: 4s; width: 11px; height: 11px; opacity: 0.5; }
.snow:nth-child(95) { left: 57%; animation-duration: 14s; animation-delay: 1s; width: 9px; height: 9px; opacity: 0.7; }
.snow:nth-child(96) { left: 67%; animation-duration: 10s; animation-delay: 5.5s; width: 5px; height: 5px; opacity: 0.8; }
.snow:nth-child(97) { left: 77%; animation-duration: 13s; animation-delay: 3.5s; width: 8px; height: 8px; opacity: 0.6; }
.snow:nth-child(98) { left: 87%; animation-duration: 9s; animation-delay: 0s; width: 10px; height: 10px; opacity: 0.9; }
.snow:nth-child(99) { left: 97%; animation-duration: 12s; animation-delay: 2.5s; width: 6px; height: 6px; opacity: 0.5; }
.snow:nth-child(100) { left: 50%; animation-duration: 15s; animation-delay: 4.5s; width: 12px; height: 12px; opacity: 0.7; }
.snow:nth-child(101) { left: 2%; animation-duration: 10s; animation-delay: 6s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(102) { left: 8%; animation-duration: 14s; animation-delay: 1s; width: 6px; height: 6px; opacity: 0.6; }
.snow:nth-child(103) { left: 13%; animation-duration: 9s; animation-delay: 3.5s; width: 11px; height: 11px; opacity: 0.9; }
.snow:nth-child(104) { left: 18%; animation-duration: 11s; animation-delay: 0s; width: 5px; height: 5px; opacity: 0.5; }
.snow:nth-child(105) { left: 23%; animation-duration: 13s; animation-delay: 5s; width: 9px; height: 9px; opacity: 0.7; }
.snow:nth-child(106) { left: 28%; animation-duration: 8s; animation-delay: 2.5s; width: 7px; height: 7px; opacity: 0.8; }
.snow:nth-child(107) { left: 33%; animation-duration: 12s; animation-delay: 4s; width: 10px; height: 10px; opacity: 0.6; }
.snow:nth-child(108) { left: 38%; animation-duration: 15s; animation-delay: 1.5s; width: 12px; height: 12px; opacity: 0.9; }
.snow:nth-child(109) { left: 43%; animation-duration: 10s; animation-delay: 6.5s; width: 6px; height: 6px; opacity: 0.5; }
.snow:nth-child(110) { left: 48%; animation-duration: 9s; animation-delay: 0.5s; width: 8px; height: 8px; opacity: 0.7; }
.snow:nth-child(111) { left: 53%; animation-duration: 14s; animation-delay: 3s; width: 11px; height: 11px; opacity: 0.8; }
.snow:nth-child(112) { left: 58%; animation-duration: 11s; animation-delay: 5.5s; width: 7px; height: 7px; opacity: 0.6; }
.snow:nth-child(113) { left: 63%; animation-duration: 8s; animation-delay: 2s; width: 9px; height: 9px; opacity: 0.9; }
.snow:nth-child(114) { left: 68%; animation-duration: 13s; animation-delay: 4.5s; width: 5px; height: 5px; opacity: 0.5; }
.snow:nth-child(115) { left: 73%; animation-duration: 12s; animation-delay: 1s; width: 10px; height: 10px; opacity: 0.7; }
.snow:nth-child(116) { left: 78%; animation-duration: 10s; animation-delay: 6s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(117) { left: 83%; animation-duration: 9s; animation-delay: 3.5s; width: 12px; height: 12px; opacity: 0.6; }
.snow:nth-child(118) { left: 88%; animation-duration: 15s; animation-delay: 0s; width: 6px; height: 6px; opacity: 0.9; }
.snow:nth-child(119) { left: 93%; animation-duration: 11s; animation-delay: 5s; width: 11px; height: 11px; opacity: 0.5; }
.snow:nth-child(120) { left: 98%; animation-duration: 14s; animation-delay: 2.5s; width: 7px; height: 7px; opacity: 0.7; }
.snow:nth-child(121) { left: 3%; animation-duration: 8s; animation-delay: 4s; width: 9px; height: 9px; opacity: 0.8; }
.snow:nth-child(122) { left: 10%; animation-duration: 13s; animation-delay: 1.5s; width: 5px; height: 5px; opacity: 0.6; }
.snow:nth-child(123) { left: 15%; animation-duration: 12s; animation-delay: 6.5s; width: 10px; height: 10px; opacity: 0.9; }
.snow:nth-child(124) { left: 20%; animation-duration: 9s; animation-delay: 0.5s; width: 8px; height: 8px; opacity: 0.5; }
.snow:nth-child(125) { left: 25%; animation-duration: 10s; animation-delay: 3s; width: 6px; height: 6px; opacity: 0.7; }
.snow:nth-child(126) { left: 30%; animation-duration: 14s; animation-delay: 5.5s; width: 12px; height: 12px; opacity: 0.8; }
.snow:nth-child(127) { left: 35%; animation-duration: 11s; animation-delay: 2s; width: 11px; height: 11px; opacity: 0.6; }
.snow:nth-child(128) { left: 40%; animation-duration: 15s; animation-delay: 4.5s; width: 7px; height: 7px; opacity: 0.9; }
.snow:nth-child(129) { left: 45%; animation-duration: 8s; animation-delay: 1s; width: 9px; height: 9px; opacity: 0.5; }
.snow:nth-child(130) { left: 50%; animation-duration: 13s; animation-delay: 6s; width: 5px; height: 5px; opacity: 0.7; }
.snow:nth-child(131) { left: 55%; animation-duration: 9s; animation-delay: 3.5s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(132) { left: 60%; animation-duration: 12s; animation-delay: 0s; width: 10px; height: 10px; opacity: 0.6; }
.snow:nth-child(133) { left: 65%; animation-duration: 10s; animation-delay: 5s; width: 6px; height: 6px; opacity: 0.9; }
.snow:nth-child(134) { left: 70%; animation-duration: 14s; animation-delay: 2.5s; width: 12px; height: 12px; opacity: 0.5; }
.snow:nth-child(135) { left: 75%; animation-duration: 11s; animation-delay: 4s; width: 7px; height: 7px; opacity: 0.7; }
.snow:nth-child(136) { left: 80%; animation-duration: 15s; animation-delay: 1.5s; width: 11px; height: 11px; opacity: 0.8; }
.snow:nth-child(137) { left: 85%; animation-duration: 8s; animation-delay: 6.5s; width: 9px; height: 9px; opacity: 0.6; }
.snow:nth-child(138) { left: 90%; animation-duration: 13s; animation-delay: 0.5s; width: 5px; height: 5px; opacity: 0.9; }
.snow:nth-child(139) { left: 95%; animation-duration: 9s; animation-delay: 3s; width: 8px; height: 8px; opacity: 0.5; }
.snow:nth-child(140) { left: 1%; animation-duration: 12s; animation-delay: 5.5s; width: 10px; height: 10px; opacity: 0.7; }
.snow:nth-child(141) { left: 7%; animation-duration: 10s; animation-delay: 2s; width: 6px; height: 6px; opacity: 0.8; }
.snow:nth-child(142) { left: 12%; animation-duration: 14s; animation-delay: 4.5s; width: 12px; height: 12px; opacity: 0.6; }
.snow:nth-child(143) { left: 17%; animation-duration: 11s; animation-delay: 1s; width: 7px; height: 7px; opacity: 0.9; }
.snow:nth-child(144) { left: 22%; animation-duration: 15s; animation-delay: 6s; width: 11px; height: 11px; opacity: 0.5; }
.snow:nth-child(145) { left: 27%; animation-duration: 8s; animation-delay: 3.5s; width: 9px; height: 9px; opacity: 0.7; }
.snow:nth-child(146) { left: 32%; animation-duration: 13s; animation-delay: 0s; width: 5px; height: 5px; opacity: 0.8; }
.snow:nth-child(147) { left: 37%; animation-duration: 9s; animation-delay: 5s; width: 8px; height: 8px; opacity: 0.6; }
.snow:nth-child(148) { left: 42%; animation-duration: 12s; animation-delay: 2.5s; width: 10px; height: 10px; opacity: 0.9; }
.snow:nth-child(149) { left: 47%; animation-duration: 10s; animation-delay: 4s; width: 6px; height: 6px; opacity: 0.5; }
.snow:nth-child(150) { left: 52%; animation-duration: 14s; animation-delay: 1.5s; width: 12px; height: 12px; opacity: 0.7; }
.snow:nth-child(151) { left: 57%; animation-duration: 11s; animation-delay: 6.5s; width: 7px; height: 7px; opacity: 0.8; }
.snow:nth-child(152) { left: 62%; animation-duration: 15s; animation-delay: 0.5s; width: 11px; height: 11px; opacity: 0.6; }
.snow:nth-child(153) { left: 67%; animation-duration: 8s; animation-delay: 3s; width: 9px; height: 9px; opacity: 0.9; }
.snow:nth-child(154) { left: 72%; animation-duration: 13s; animation-delay: 5.5s; width: 5px; height: 5px; opacity: 0.5; }
.snow:nth-child(155) { left: 77%; animation-duration: 9s; animation-delay: 2s; width: 8px; height: 8px; opacity: 0.7; }
.snow:nth-child(156) { left: 82%; animation-duration: 12s; animation-delay: 4.5s; width: 10px; height: 10px; opacity: 0.8; }
.snow:nth-child(157) { left: 87%; animation-duration: 10s; animation-delay: 1s; width: 6px; height: 6px; opacity: 0.6; }
.snow:nth-child(158) { left: 92%; animation-duration: 14s; animation-delay: 6s; width: 12px; height: 12px; opacity: 0.9; }
.snow:nth-child(159) { left: 97%; animation-duration: 11s; animation-delay: 3.5s; width: 7px; height: 7px; opacity: 0.5; }
.snow:nth-child(160) { left: 4%; animation-duration: 15s; animation-delay: 0s; width: 11px; height: 11px; opacity: 0.7; }
.snow:nth-child(161) { left: 9%; animation-duration: 8s; animation-delay: 5s; width: 9px; height: 9px; opacity: 0.8; }
.snow:nth-child(162) { left: 14%; animation-duration: 13s; animation-delay: 2.5s; width: 5px; height: 5px; opacity: 0.6; }
.snow:nth-child(163) { left: 19%; animation-duration: 9s; animation-delay: 4s; width: 8px; height: 8px; opacity: 0.9; }
.snow:nth-child(164) { left: 24%; animation-duration: 12s; animation-delay: 1.5s; width: 10px; height: 10px; opacity: 0.5; }
.snow:nth-child(165) { left: 29%; animation-duration: 10s; animation-delay: 6.5s; width: 6px; height: 6px; opacity: 0.7; }
.snow:nth-child(166) { left: 34%; animation-duration: 14s; animation-delay: 0.5s; width: 12px; height: 12px; opacity: 0.8; }
.snow:nth-child(167) { left: 39%; animation-duration: 11s; animation-delay: 3s; width: 7px; height: 7px; opacity: 0.6; }
.snow:nth-child(168) { left: 44%; animation-duration: 15s; animation-delay: 5.5s; width: 11px; height: 11px; opacity: 0.9; }
.snow:nth-child(169) { left: 49%; animation-duration: 8s; animation-delay: 2s; width: 9px; height: 9px; opacity: 0.5; }
.snow:nth-child(170) { left: 54%; animation-duration: 13s; animation-delay: 4.5s; width: 5px; height: 5px; opacity: 0.7; }
.snow:nth-child(171) { left: 59%; animation-duration: 9s; animation-delay: 1s; width: 8px; height: 8px; opacity: 0.8; }
.snow:nth-child(172) { left: 64%; animation-duration: 12s; animation-delay: 6s; width: 10px; height: 10px; opacity: 0.6; }
.snow:nth-child(173) { left: 69%; animation-duration: 10s; animation-delay: 3.5s; width: 6px; height: 6px; opacity: 0.9; }
.snow:nth-child(174) { left: 74%; animation-duration: 14s; animation-delay: 0s; width: 12px; height: 12px; opacity: 0.5; }
.snow:nth-child(175) { left: 79%; animation-duration: 11s; animation-delay: 5s; width: 7px; height: 7px; opacity: 0.7; }
.snow:nth-child(176) { left: 84%; animation-duration: 15s; animation-delay: 2.5s; width: 11px; height: 11px; opacity: 0.8; }
.snow:nth-child(177) { left: 89%; animation-duration: 8s; animation-delay: 4s; width: 9px; height: 9px; opacity: 0.6; }
.snow:nth-child(178) { left: 94%; animation-duration: 13s; animation-delay: 1.5s; width: 5px; height: 5px; opacity: 0.9; }
.snow:nth-child(179) { left: 99%; animation-duration: 9s; animation-delay: 6.5s; width: 8px; height: 8px; opacity: 0.5; }
.snow:nth-child(180) { left: 5%; animation-duration: 12s; animation-delay: 0.5s; width: 10px; height: 10px; opacity: 0.7; }
.snow:nth-child(181) { left: 11%; animation-duration: 10s; animation-delay: 3s; width: 6px; height: 6px; opacity: 0.8; }
.snow:nth-child(182) { left: 16%; animation-duration: 14s; animation-delay: 5.5s; width: 12px; height: 12px; opacity: 0.6; }
.snow:nth-child(183) { left: 21%; animation-duration: 11s; animation-delay: 2s; width: 7px; height: 7px; opacity: 0.9; }
.snow:nth-child(184) { left: 26%; animation-duration: 15s; animation-delay: 4.5s; width: 11px; height: 11px; opacity: 0.5; }
.snow:nth-child(185) { left: 31%; animation-duration: 8s; animation-delay: 1s; width: 9px; height: 9px; opacity: 0.7; }
.snow:nth-child(186) { left: 36%; animation-duration: 13s; animation-delay: 6s; width: 5px; height: 5px; opacity: 0.8; }
.snow:nth-child(187) { left: 41%; animation-duration: 9s; animation-delay: 3.5s; width: 8px; height: 8px; opacity: 0.6; }
.snow:nth-child(188) { left: 46%; animation-duration: 12s; animation-delay: 0s; width: 10px; height: 10px; opacity: 0.9; }
.snow:nth-child(189) { left: 51%; animation-duration: 10s; animation-delay: 5s; width: 6px; height: 6px; opacity: 0.5; }
.snow:nth-child(190) { left: 56%; animation-duration: 14s; animation-delay: 2.5s; width: 12px; height: 12px; opacity: 0.7; }
.snow:nth-child(191) { left: 61%; animation-duration: 11s; animation-delay: 4s; width: 7px; height: 7px; opacity: 0.8; }
.snow:nth-child(192) { left: 66%; animation-duration: 15s; animation-delay: 1.5s; width: 11px; height: 11px; opacity: 0.6; }
.snow:nth-child(193) { left: 71%; animation-duration: 8s; animation-delay: 6.5s; width: 9px; height: 9px; opacity: 0.9; }
.snow:nth-child(194) { left: 76%; animation-duration: 13s; animation-delay: 0.5s; width: 5px; height: 5px; opacity: 0.5; }
.snow:nth-child(195) { left: 81%; animation-duration: 9s; animation-delay: 3s; width: 8px; height: 8px; opacity: 0.7; }
.snow:nth-child(196) { left: 86%; animation-duration: 12s; animation-delay: 5.5s; width: 10px; height: 10px; opacity: 0.8; }
.snow:nth-child(197) { left: 91%; animation-duration: 10s; animation-delay: 2s; width: 6px; height: 6px; opacity: 0.6; }
.snow:nth-child(198) { left: 96%; animation-duration: 14s; animation-delay: 4.5s; width: 12px; height: 12px; opacity: 0.9; }
.snow:nth-child(199) { left: 0%; animation-duration: 11s; animation-delay: 1s; width: 7px; height: 7px; opacity: 0.5; }
.snow:nth-child(200) { left: 100%; animation-duration: 15s; animation-delay: 6s; width: 11px; height: 11px; opacity: 0.7; }

@keyframes snowfall {
  0% {
    transform: translateY(-10px) rotate(0deg);
    opacity: 1;
  }
  100% {
    transform: translateY(100vh) rotate(360deg);
    opacity: 0.3;
  }
}

.card {
  position: relative;
  z-index: 10;
  background: transparent;
  padding: 3rem 2.5rem;
  text-align: center;
  max-width: 90%;
  width: 400px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.title {
  font-family: 'Fredoka One', cursive;
  font-size: 3.5rem;
  font-weight: 400;
  color: #ff0000;
  margin-bottom: 3rem;
  letter-spacing: 2px;
  background: rgba(255, 255, 255, 0.95);
  padding: 1rem 1.5rem;
  padding-left: calc(1.5rem + 2px);
  border-radius: 20px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  text-shadow:
    0 4px 0 #b30000,
    0 5px 0 #990000,
    0 6px 0 #800000,
    0 7px 0 #660000,
    0 8px 0 #4d0000,
    0 9px 0 #330000,
    0 10px 10px rgba(0, 0, 0, 0.4);
  display: inline-block;
  max-width: 100%;
  min-width: 340px;
  text-align: center;
}

.button-container {
  min-height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.loading-button {
  position: relative;
  background: linear-gradient(180deg, #ff6666 0%, #ff0000 50%, #cc0000 100%);
  border: 4px solid #990000;
  padding: 0;
  width: 320px;
  height: 50px;
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.2s ease;
  box-shadow:
    0 4px 8px rgba(0, 0, 0, 0.3),
    inset 0 2px 4px rgba(255, 255, 255, 0.3);
  overflow: hidden;
}

.button-text {
  position: relative;
  z-index: 2;
  font-family: 'Fredoka One', cursive;
  font-size: 1.1rem;
  font-weight: 400;
  color: #ffffff;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}

.loading-button:hover {
  transform: scale(1.02);
  box-shadow:
    0 6px 12px rgba(0, 0, 0, 0.35),
    inset 0 2px 4px rgba(255, 255, 255, 0.5);
}

.loading-button:active {
  transform: scale(0.98);
  box-shadow:
    0 2px 4px rgba(0, 0, 0, 0.3),
    inset 0 2px 4px rgba(255, 255, 255, 0.5);
}

.loading-bar {
  position: relative;
  width: 340px;
  height: 55px;
  background: linear-gradient(180deg, #ff6666 0%, #ff0000 50%, #cc0000 100%);
  border: 4px solid #990000;
  border-radius: 28px;
  margin-top: 1.5rem;
  overflow: hidden;
  box-shadow:
    0 4px 8px rgba(0, 0, 0, 0.3),
    inset 0 2px 4px rgba(255, 255, 255, 0.3);
}

.loading-bar-fill {
  position: absolute;
  left: 5px;
  top: 50%;
  transform: translateY(-50%);
  width: 40px;
  max-width: calc(100% - 10px);
  height: 40px;
  background: linear-gradient(180deg, #ffffff 0%, #f0f0f0 50%, #e0e0e0 100%);
  border-radius: 20px;
  box-shadow: inset 0 2px 4px rgba(255, 255, 255, 0.8);
  animation: fill-progress 35s linear forwards;
}

@keyframes fill-progress {
  0% {
    width: 40px;
  }
  100% {
    width: calc(100% - 10px);
  }
}

.loading-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: 'Fredoka One', cursive;
  font-size: 0.9rem;
  color: #ffffff;
  text-shadow:
    -1px -1px 0 #000,
    1px -1px 0 #000,
    -1px 1px 0 #000,
    1px 1px 0 #000,
    -1px 0 0 #000,
    1px 0 0 #000,
    0 -1px 0 #000,
    0 1px 0 #000;
  z-index: 2;
  white-space: nowrap;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 100;
  padding: 1rem;
}

.modal {
  background: linear-gradient(180deg, #ffffff 0%, #f5f5f5 100%);
  padding: 2.5rem 2rem;
  border-radius: 30px;
  border: 5px solid #cc0000;
  max-width: 90%;
  width: 380px;
  text-align: center;
  box-shadow:
    0 8px 24px rgba(0, 0, 0, 0.3),
    inset 0 2px 4px rgba(255, 255, 255, 0.5);
}

.modal-text {
  font-family: 'Fredoka One', cursive;
  font-size: 1.2rem;
  color: #cc0000;
  line-height: 1.6;
  margin-bottom: 1rem;
  font-weight: 400;
}

.modal-subtext {
  font-size: 1rem;
  color: #990000;
  margin-bottom: 2rem;
  font-style: italic;
  font-weight: 500;
}

.modal-button {
  background: linear-gradient(180deg, #ff6666 0%, #ff0000 50%, #cc0000 100%);
  color: white;
  border: 3px solid #990000;
  padding: 0.8rem 2.5rem;
  font-family: 'Fredoka One', cursive;
  font-size: 1.1rem;
  font-weight: 400;
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.2s ease;
  box-shadow:
    0 4px 8px rgba(0, 0, 0, 0.3),
    inset 0 2px 4px rgba(255, 255, 255, 0.3);
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
}

.modal-button:hover {
  transform: scale(1.05);
  box-shadow:
    0 6px 12px rgba(0, 0, 0, 0.35),
    inset 0 2px 4px rgba(255, 255, 255, 0.3);
}

.modal-button:active {
  transform: scale(0.98);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active .modal,
.fade-leave-active .modal {
  transition: transform 0.25s ease, opacity 0.25s ease;
}

.fade-enter-from .modal,
.fade-leave-to .modal {
  transform: scale(0.95);
  opacity: 0;
}

.fade-button-enter-active,
.fade-button-leave-active {
  transition: opacity 0.4s ease;
}

.fade-button-enter-from,
.fade-button-leave-to {
  opacity: 0;
}

@media (min-width: 768px) {
  .card {
    padding: 3.5rem 3rem;
    width: 500px;
  }

  .title {
    font-size: 5rem;
    letter-spacing: 6px;
    padding: 1.5rem 3rem;
    padding-left: calc(3rem + 6px);
    min-width: auto;
    width: auto;
  }

  .loading-button {
    width: 420px;
    height: 55px;
  }

  .loading-bar {
    width: 420px;
  }

  .button-text {
    font-size: 1.2rem;
  }
}
</style>
