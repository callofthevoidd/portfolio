<script setup lang="ts">

defineProps({ userId: String })
</script>

<template>
  <div class="profile">
   <div class="profile-data">
     <img v-bind:src="profileLink" v-on:click="secret()" class="profile-img"></img>
     <div class="profile-names">
      <h1 class="name-label animated-text">callofthevoid</h1>
      <h2 class="username-label">@callofthevoidd</h2>
      <div class="social-links">
        <a target="_blank" href="https://discord.com/users/1221457893522669662" style="background-color: transparent;">
          <img class="disc-icon" style="width: 3rem; height: 3rem; background-color: transparent; aspect-ratio: 1/1;"
          src="https://cdn-icons-png.flaticon.com/512/5968/5968756.png"
          ></a>

        <a target="_blank" href="https://www.youtube.com/@ivadsiuls" style="background-color: transparent;">
          <img class="yt-icon" style="width: 3rem; height: 3rem; background-color: transparent; aspect-ratio: 1/1;"
          src="https://upload.wikimedia.org/wikipedia/commons/5/59/Empty.png"
          ></a>

       <a target="_blank" href="https://www.roblox.com/users/5048508312/profile" style="background-color: transparent;">
          <img class="rblx-icon" style="width: 2.5rem; height: 2.5rem; background-color: transparent; aspect-ratio: 1/1;"
          src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Roblox_icon_-_2017.svg/500px-Roblox_icon_-_2017.svg.png"
          ></a>

       <a target="_blank" href="https://github.com/callofthevoidd" style="background-color: transparent;">
          <img class="gh-icon" style="width: 2.5rem; height: 2.5rem; background-color: transparent; aspect-ratio: 1/1;"
          src="https://cdn-icons-png.flaticon.com/512/2111/2111432.png"
          ></a>
      </div>
     </div>
   </div>
   <hr>
   <p class="status-text">
    I've been programming since <strong>2019</strong>, primarily using <strong>Luau</strong> to develop games and contribute to open source projects on <strong>Roblox</strong>.

   <br>
    Over the years, I’ve built experience in multiple languages, including <strong>JavaScript</strong> and <strong>basic Python</strong>.

    <br>
    While I mostly work within the Roblox ecosystem, I'm currently expanding into <strong>C/C++</strong> to create desktop applications and games on other engines.
   </p>
  </div>
</template>

<script lang="ts">
export default {
    data() {
        return {
            profileLink: `https://static.vecteezy.com/system/resources/previews/009/292/244/non_2x/default-avatar-icon-of-social-media-user-vector.jpg`,
            EVILsiuls: false,
        }
    },

    watch: {
      EVILsiuls: {
        handler(theme) {
          document.documentElement.setAttribute("data-secret1", theme);
        },
        immediate: true,
      },
    },

    methods: {
      secret() {
        this.EVILsiuls = !this.EVILsiuls

        if (this.EVILsiuls) {
          alert("wowwie you found the supah secret EVILvoid option thats supah secret and crazy and scary")
        }
      },
    },

    mounted() {
        fetch(`https://avatar-cyan.vercel.app/api/${this.userId}`).then(response => response.json()).then(data => {
            this.profileLink = data.avatarUrl
        })
    }
}
</script>

<style scoped>
.profile {
  height: 70vh;
  width: 45vw;
  justify-self: left;

  display: flex;
  flex-direction: column;

  justify-content: left;

  border-radius: 2rem;

  gap: 1rem;

  padding-top: 2rem;

  background-color: var(--clr-frame);
  box-shadow: 0px 7px 7px rgba(13, 8, 0, 0.249);
}

@media (max-width: 1200px) {
  /* tablet styles here */
  .profile {
    width: 90vw;
  }
}

.status-text {
  color: var(--clr-text);
  font-size: 1.7rem;
  font-weight: 500;

  margin: 0;

  line-height: 1.6;

  padding-left: 2rem;
  padding-right: 2rem;
}

.profile-data {
  display: flex;
  flex-direction: row;

  gap: 1.5rem;

  margin-left: 2rem;
  flex-wrap: wrap;
}

.profile-names {
  display: flex;
  flex-direction: column;

  gap: 0rem;

  justify-content: center;
  align-items: flex-start;
  flex-wrap: wrap;
}

.profile-img {
  width: 10vw;
  height: 10vw;
  border-radius: 50%;
  aspect-ratio: 1 / 1;
}

.name-label {
    color: var(--clr-text);

    font-size: clamp(3rem, 3.5rem, 5rem);

    margin: 0rem;
    white-space: normal;
    overflow-wrap: break-word;
}

.username-label {
    color: var(--clr-secondary-text);
    font-weight: 600;

    font-size: 2.3rem;

    margin: 0rem;
}

@media (max-width: 1200px) {
  /* tablet styles here */
  .name-label {
    font-size: clamp(2rem, 2.2rem, 4rem);
  }
  .username-label {
    font-size: 1.5rem;
  }
  .profile-img {
    width: 25vw;
    height: 25vw;
  }
}

.animated-text {
  font-family: "Arial", sans-serif;
  animation: fontChange 2s infinite;
}

.social-links {
  display: flex;
  gap: 0.5rem;

  align-items: center;
}

.rblx-icon {
  filter: brightness(0);
}

.yt-icon {
  background-image: url("https://cdn3.iconfinder.com/data/icons/social-network-30/512/social-06-512.png");

  background-size: cover;

  background-repeat: no-repeat;

  background-position: center;
}

[data-theme="dark"] {
  .disc-icon {
    filter: brightness(0) invert(1);
  }

  .rblx-icon {
    filter: brightness(0) invert(1);
  }

  .yt-icon {
    background-image: url("https://assets.streamlinehq.com/image/private/w_300,h_300,ar_1/f_auto/v1/icons/c4/logo-youtube-9uz0vchu8rnpddaet2viom.png/logo-youtube-x5qkxw19tzce323872cxy5.png?_a=DATAg1AAZAA0");

    filter: brightness(0) invert(1);
  }

  .gh-icon {
    filter: brightness(0) invert(1);
  }
}

@keyframes fontChange {
  0%   { font-family: "Arial", sans-serif; }
  25%  { font-family: "Courier New", monospace; }
  50%  { font-family: "Georgia", serif; }
  75%  { font-family: "Comic Sans MS", cursive; }
  100% { font-family: "Arial", sans-serif; }
}
</style>
