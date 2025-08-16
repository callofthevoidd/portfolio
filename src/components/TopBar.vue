<script setup lang="ts"></script>

<template>
  <div class="top-bar top-centered">
    <h2 class="unix-label">{{ unixTime }}</h2>
    <h2 class="main-label">{{ date }}</h2>
    <h2 class="current-time-label">{{ currentTime }}</h2>
    <button class="theme-selector" v-on:click="switchTheme()">
      <img
        class="theme-img"
        src="https://ewe3rn3et5.ufs.sh/f/O2pVoxcml58RX70sthHaO6sunRqcPBkQNYd1AbVp9fWhCerF"
      />
    </button>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      date: `Loading...`,
      unixTime: `Loading...`,
      currentTime: `Loading...`,
      theme: localStorage.getItem("theme") ?? `light`,
    };
  },
  watch: {
    theme: {
      handler(theme) {
        document.documentElement.setAttribute("data-theme", theme);
        localStorage.setItem("theme", theme);
      },
      immediate: true,
    },
  },
  methods: {
    switchTheme() {
      if (this.theme == `light`) {
        this.theme = `dark`;
      } else {
        this.theme = `light`;
      }
    },
    getDate() {
      const today = new Date();

      const day = today.getDate();
      const month = today.getMonth() + 1; // Months are 0-based
      const year = today.getFullYear();

      const formattedDate = `${day}/${month}/${year}`;

      return formattedDate;
    },
    getUnixTime() {
      const unixTime = Math.floor(Date.now() / 1000);

      return unixTime;
    },
    getCurrentTime() {
      const now = new Date();

      let hours = now.getHours().toString();
      let minutes = now.getMinutes().toString();
      let seconds = now.getSeconds().toString();

      // Add leading zeros if needed
      hours = String(hours).padStart(2, "0");
      minutes = String(minutes).padStart(2, "0");
      seconds = String(seconds).padStart(2, "0");

      return `${hours}:${minutes}:${seconds}`;
    },
    updLoop() {
      this.date = this.getDate();
      this.unixTime = this.getUnixTime().toString();
      this.currentTime = this.getCurrentTime();

      setTimeout(() => {
        this.updLoop();
      }, 1000);
    },
  },

  mounted() {
    this.updLoop();
  },
};
</script>

<style scoped>
.top-bar {
  height: 10vh;
  width: 100%;
  justify-self: center;

  display: flex;

  justify-content: center;
  align-items: center;

  border-radius: 2rem;

  gap: 1rem;

  background-color: var(--clr-frame);
  box-shadow: 0px 7px 7px rgba(13, 8, 0, 0.249);
}

.main-label {
  color: var(--clr-text);
  font-size: clamp(24px, 1.8vw, 48px);

  text-align: center;
}

.unix-label {
  display: flex;
  color: var(--clr-text);
  transform: translateY(-0.4vh);

  font-size: clamp(16px, 1.3vw, 48px);
}

.current-time-label {
  display: flex;
  color: var(--clr-text);
  transform: translateY(-0.4vh);

  font-size: clamp(16px, 1.3vw, 48px);
}

.theme-selector {
  width: 2.7%;
  aspect-ratio: 1 / 1;
  background-color: var(--clr-secondary-frame);
  color: var(--clr-text);

  transition: transform 0.3s ease;

  outline: 0;
  position: relative;
  padding: 0.1rem;

  left: 33%;
}

.theme-img {
  object-fit: cover;
  width: 90%;
  height: 90%;
  aspect-ratio: 1 / 1;
  transition: transform 0.3s ease;

  justify-self: center;
}

[data-theme="dark"] {
  .theme-img {
    filter: grayscale(100%) brightness(0) invert(1);
    transform: scaleX(-1);
  }
}
</style>
