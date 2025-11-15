<script setup lang="ts">
import { ref, onMounted } from 'vue'

const showModal = ref<boolean>(false)
const isLoading = ref<boolean>(true)
const loadingTextIndex = ref<number>(0)

const loadingTexts = [
  "Loading Switzerland…",
  "Don't worry, won't take long…",
  "Only 9,051,029 residents to check…",
  "Counting chocolate factories…",
  "Syncing with Alps…",
  "Calibrating cheese holes…",
  "Polishing watches…",
  "Yodeling initialization…",
  "Banking your data securely…",
  "Neutralizing information…",
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
            Oops… this feature unlocks only after a real life Switzerland visit.
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
  font-size: 4.5rem;
  font-weight: 400;
  color: #ff0000;
  margin-bottom: 3rem;
  letter-spacing: 4px;
  background: rgba(255, 255, 255, 0.95);
  padding: 1rem 2rem;
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
  width: 0%;
  max-width: calc(100% - 10px);
  height: 40px;
  background: linear-gradient(180deg, #ffffff 0%, #f0f0f0 50%, #e0e0e0 100%);
  border-radius: 20px;
  box-shadow: inset 0 2px 4px rgba(255, 255, 255, 0.8);
  animation: fill-progress 30s linear forwards;
}

@keyframes fill-progress {
  0% {
    width: 0%;
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
  }

  .title {
    font-size: 5rem;
  }

  .loading-button {
    width: 380px;
    height: 55px;
  }

  .button-text {
    font-size: 1.2rem;
  }
}
</style>
