<script setup lang="ts">

defineProps({ userId: String })
</script>

<template>
  <div class="profile">
    <img v-bind:src="profileLink" class="profile-img"></img>
    <h1 class="name-label">callofthevoid</h1>
    <h2 class="name-label">@callofthevoidd</h2>
  </div>
</template>

<script lang="ts">
export default {
    data() {
        return {
            profileLink: `https://static.vecteezy.com/system/resources/previews/009/292/244/non_2x/default-avatar-icon-of-social-media-user-vector.jpg`
        }
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
  width: 40%;
  justify-self: left;

  display: flex;

  justify-content: left;

  border-radius: 2rem;

  gap: 1rem;

  padding-top: 2rem;
  padding-left: 2rem;

  background-color: var(--clr-frame);
  box-shadow: 0px 7px 7px rgba(13, 8, 0, 0.249);
}

.profile-img {
    width: 25%;
    height: 25%;

    aspect-ratio: 1 / 1;

    border-radius: 3000rem;
    
    box-shadow: 0px 6px 3px rgba(99, 99, 99, 0.471);
}

.name-label {
    color: var(--clr-text);
    text-shadow: 0px 3px 3px rgba(99, 99, 99, 0.343);
}
</style>
