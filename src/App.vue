<script setup>
import AddPatient from './components/AddPatient.vue'
import ViewAllPatient from './components/ViewAllPatient.vue'
</script>

<template>
  <header>
    <h1>Patient Manager</h1>
  </header>
  <main>
    <div class="panel">
      <AddPatient />
    </div>
    <div class="panel">
      <ViewAllPatient />
    </div>
  </main>
  <div id="bubble-background">
    <div class="bubble" id="b1"></div>
    <div class="bubble" id="b2"></div>
    <div class="bubble" id="b3"></div>
    <div class="bubble" id="b4"></div>
    <div class="bubble" id="b5"></div>
  </div>
</template>
<style scoped>
main {
  display: flex;
  height: calc(100vh - 60px);
  width: 100%;
  overflow: hidden;
}

main > div {
  flex: 1;
  transition: flex 0.4s ease;
  overflow-y: auto;
  border: 1px solid #ccc;
}

main > div:hover {
  flex: 2;
}

h1 {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60px;
  font-size: 3rem;
  font-weight: 700;
  color: var(--text-primary);
  text-align: center;
}

/*background animation*/
#bubble-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  overflow: hidden;
  pointer-events: none;
}

.bubble {
  position: absolute;
  border-radius: 50%;
  opacity: 0.15;
  animation: floatRandom 20s infinite ease-in-out alternate;
}

@keyframes floatRandom {
  0% {
    transform: translate(random(-100px,100px), random(-100px,100px)) scale(1);
    opacity: 0.1;
  }
  25% {
    transform: translate(100px, -50px) scale(1.1);
    opacity: 0.2;
  }
  50% {
    transform: translate(-80px, 100px) scale(1.05);
    opacity: 0.25;
  }
  75% {
    transform: translate(50px, -80px) scale(1.15);
    opacity: 0.2;
  }
  100% {
    transform: translate(-100px, 60px) scale(1.2);
    opacity: 0.1;
  }
}

#b1 {
  width: 180px;
  height: 180px;
  background: #93c5fd;
  top: 10%;
  left: 15%;
  animation-duration: 28s;
}

#b2 {
  width: 120px;
  height: 120px;
  background: #60a5fa;
  top: 30%;
  left: 60%;
  animation-duration: 24s;
}

#b3 {
  width: 200px;
  height: 200px;
  background: #3b82f6;
  top: 50%;
  left: 40%;
  animation-duration: 30s;
}

#b4 {
  width: 140px;
  height: 140px;
  background: #2563eb;
  top: 70%;
  left: 20%;
  animation-duration: 26s;
}

#b5 {
  width: 160px;
  height: 160px;
  background: #1d4ed8;
  top: 20%;
  left: 80%;
  animation-duration: 32s;
}
</style>
