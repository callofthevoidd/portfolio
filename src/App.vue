<script setup lang="ts">
import Profile from "./components/Profile.vue";
import Stuff from "./components/Stuff.vue";
import TopBar from "./components/TopBar.vue";
</script>

<template>
  <TopBar />
  <div class="main">
    <Profile user-id="1221457893522669662" />
    <Stuff />
  </div>
</template>

<style scoped>
.main {
  width: 90vw;
  height: 84vh;
  display: flex;
  align-self: flex-start;

  padding-top: 2rem;
  margin-bottom: 2rem;

  gap: 2rem;
}

@media (max-width: 1200px) {
  /* tablet styles here */
  .main {
    flex-direction: column;
  }
}

.content {
  display: flex;
  width: 100%;
  height: 70vh; /* remaining height under topbar */
  align-items: center;
}
</style>
