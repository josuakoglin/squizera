<script setup lang="ts">
import { ref } from 'vue'

const showModal = ref<boolean>(false)

const openModal = (): void => {
  showModal.value = true
}

const closeModal = (): void => {
  showModal.value = false
}
</script>

<template>
  <div class="background">
    <div class="sky"></div>
    <div class="mountains"></div>

    <div class="card">
      <h1 class="title">SQUIZERA</h1>
      <button class="primary-button" @click="openModal">
        Tap to Suizify
      </button>
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
@import url('https://fonts.googleapis.com/css2?family=Bangers&display=swap');

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

.mountains {
  display: none;
}

.card {
  position: relative;
  z-index: 10;
  background: transparent;
  padding: 3rem 2.5rem;
  border-radius: 30px;
  border: none;
  box-shadow: none;
  text-align: center;
  max-width: 90%;
  width: 360px;
}

.title {
  font-family: 'Bangers', cursive;
  font-size: 3rem;
  font-weight: 900;
  color: #ff2d2d;
  margin-bottom: 1.5rem;
  letter-spacing: 2px;
  -webkit-text-stroke: 3px #000;
  text-shadow:
    -3px -3px 0 #fff,
    3px -3px 0 #fff,
    -3px 3px 0 #fff,
    3px 3px 0 #fff,
    -3px 0 0 #fff,
    3px 0 0 #fff,
    0 -3px 0 #fff,
    0 3px 0 #fff,
    5px 5px 0 #fbb6ce;
}

.primary-button {
  background: #fbbf24;
  color: #000;
  border: 5px solid #000;
  padding: 1.2rem 3rem;
  font-size: 1.3rem;
  font-weight: 900;
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.2s ease;
  box-shadow:
    6px 6px 0 #000,
    inset 0 -4px 0 rgba(0, 0, 0, 0.2);
  min-width: 220px;
  text-shadow: 2px 2px 0 rgba(255, 255, 255, 0.5);
  transform: rotate(-2deg);
  outline: 3px solid #fff;
  outline-offset: -8px;
}

.primary-button:hover {
  background: #f59e0b;
  transform: rotate(-2deg) translate(-2px, -2px);
  box-shadow:
    8px 8px 0 #000,
    inset 0 -4px 0 rgba(0, 0, 0, 0.2);
}

.primary-button:active {
  transform: rotate(-2deg) translate(2px, 2px);
  box-shadow:
    3px 3px 0 #000,
    inset 0 -4px 0 rgba(0, 0, 0, 0.2);
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
  background: white;
  padding: 2.5rem 2rem;
  border-radius: 25px;
  border: 4px solid #2d3748;
  max-width: 90%;
  width: 380px;
  text-align: center;
  box-shadow: 8px 8px 0 #2d3748;
}

.modal-text {
  font-size: 1.15rem;
  color: #e53e3e;
  line-height: 1.6;
  margin-bottom: 1rem;
  font-weight: 700;
  text-shadow: 1px 1px 0 #fed7d7;
}

.modal-subtext {
  font-size: 0.95rem;
  color: #553c9a;
  margin-bottom: 2rem;
  font-style: italic;
  font-weight: 600;
}

.modal-button {
  background: #48bb78;
  color: white;
  border: 3px solid #1a202c;
  padding: 0.8rem 2rem;
  font-size: 1rem;
  font-weight: 800;
  border-radius: 16px;
  cursor: pointer;
  transition: all 0.2s ease;
  box-shadow: 4px 4px 0 #1a202c;
  text-shadow: 1px 1px 0 rgba(0, 0, 0, 0.3);
}

.modal-button:hover {
  background: #38a169;
  transform: translate(-2px, -2px);
  box-shadow: 6px 6px 0 #1a202c;
}

.modal-button:active {
  transform: translate(2px, 2px);
  box-shadow: 2px 2px 0 #1a202c;
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

@media (min-width: 768px) {
  .card {
    padding: 3.5rem 3rem;
  }

  .title {
    font-size: 3.5rem;
  }
}
</style>
