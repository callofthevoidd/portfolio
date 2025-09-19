<script setup lang="ts">
import { nextTick } from "vue";
import vr from "./Utility/vr.vue";
</script>

<template>
  <div class="stuff">
    <h1 class="what-i-do">What I do</h1>
    <hr />

    <div class="language-div">
      <img class="language-img" src="https://files.catbox.moe/cxn9ps.png" />
      <vr />
      <p>
        I've been programming on Roblox for the past 6+ years and have fully
        mastered Luau.
      </p>
    </div>
    <div class="language-div">
      <img class="language-img" src="https://files.catbox.moe/kkya1w.png" />
      <vr />
      <p>
        Currently learning, hope to use this as my primary programming language
        someday.
      </p>
    </div>
    <div class="language-div">
      <img class="ts-js-img" src="https://files.catbox.moe/abtaj0.png" />
      <vr />
      <p>
        Only use these when I need to. They're fine but I prefer not to use
        them.
      </p>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  methods: {
    fitText(text: HTMLParagraphElement, container: HTMLElement) {
      const rootFontSize = parseFloat(
        getComputedStyle(document.documentElement).fontSize
      );

      let fontSizePx = 27.2; // starting font size in pixels
      text.style.fontSize = fontSizePx / rootFontSize + "rem";

      while (text.scrollHeight > container.clientHeight && fontSizePx > 5) {
        text.style.fontSize = fontSizePx / rootFontSize + "rem";
        fontSizePx--;
      }
    },
  },
  mounted() {
    window.addEventListener("resize", () => {
      const paragraphs = document.querySelectorAll("p");
      paragraphs.forEach((p) => {
        if (p.parentElement) {
          this.fitText(p, p.parentElement);
        }
      });
    });
  },
};
</script>

<style scoped>
.stuff {
  height: 70vh;
  width: 60vw;
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
  .stuff {
    width: 90vw;
  }
}

hr {
  margin: 0;
}

.what-i-do {
  color: var(--clr-text);
  margin: 0;
}

.language-div {
  display: flex;
  flex-direction: row;

  height: 20%;

  margin-top: 0.5rem;
  margin-bottom: 0.5rem;

  margin-left: 5rem;
}

.language-img {
  width: 7vw;
  height: 7vw;

  aspect-ratio: 1 / 1;

  margin-bottom: 0;

  margin-right: 5rem;
}

.ts-js-img {
  width: 11vw;
  height: 7vw;

  margin-bottom: 0;

  margin-right: 0rem;

  border-radius: 2rem;
}

p {
  font-weight: 500;
  font-size: 1.7rem;
  color: var(--clr-secondary-text);

  text-align: left;
}

@media (max-width: 1200px) {
  p {
    font-size: 1rem;
  }
}
</style>
