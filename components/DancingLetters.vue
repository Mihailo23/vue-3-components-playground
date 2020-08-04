<template>
  <h1 class="message">
    <span
      v-for="(letter, index) in letters"
      :key="index"
      :style="`--index: ${index}`"
      :data-letter="letter"
      v-text="letter"
    />
  </h1>
</template>

<script>
export default {
  name: 'DancingLetters',
  props: {
    text: {
      type: String,
      default: 'Mihailo',
    },
  },
  computed: {
    letters() {
      return this.text.split('')
    },
  },
}
</script>
<style>
:root {
  --move: 50px;
}
.message {
  font-size: 3rem;
  font-family: 'Roboto Mono', monospace;
  margin-bottom: var(--move);
}
.message span {
  display: inline-block;
  --hue: calc((360 / 7) * var(--index));
  color: hsl(var(--hue), 20%, 65%);
  font-variation-settings: 'wght' 200;
  transition: all 0.25s ease;
  animation: breathe 2.5s infinite;
  animation-delay: calc(60ms * var(--index));
}

.message span::after {
  content: attr(data-letter);
  display: block;
  position: absolute;
  top: 0.25rem;
  left: 0.25rem;
  opacity: 0.5;
}

@keyframes breathe {
  50% {
    font-variation-settings: 'wght' 700;
    color: hsl(var(--hue), 80%, 65%);
    transform: translateY(var(--move));
  }
}
</style>
