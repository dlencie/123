<template>
  <div>

    <video autoplay muted loop class="background-video">
      <source src="../assets/Network.mp4" type="video/mp4" />
    </video>

    <div class="intro-text-container">
      <h1 class="title">Save your Video in MyTube</h1>
      <h2 class="sub-title">무료 동영상 저장 서비스</h2>

      <div class="buttons-container">
        <router-link to="/search">
          <button type="button" class="btn btn-primary">동영상 검색</button>
        </router-link>
        <router-link to="/later">
          <button type="button" class="btn btn-warning">나중에 볼 동영상</button>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script setup>

</script>

<style scoped>
.background-video {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
}

.intro-text-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  color: white;
  z-index: 1;
}

.title {
  font-weight: bold;
  font-size: 3rem;
  margin: 0;
}

.sub-title {
  margin-top: 20px;
  font-size: 1.5rem;
}

.buttons-container {
  margin-top: 40px;
  display: flex;
  justify-content: center;
  gap: 20px;
}

button {
  padding: 10px 20px;
  font-size: 1rem;
  border-radius: 5px;
  transition: all 0.3s ease;
}

.btn-primary {
  background-color: #007bff;
  border: none;
}

.btn-warning {
  background-color: #ffc107;
  border: none;
}

button:hover {
  opacity: 0.8;
}

@media (max-width: 768px) {
  .title {
    font-size: 2.5rem;
  }

  .sub-title {
    font-size: 1.2rem;
  }

  .buttons-container {
    flex-direction: column;
    width: 200px;
  }

  button {
    width: 100%;
    margin-bottom: 10px;
  }
}
</style>