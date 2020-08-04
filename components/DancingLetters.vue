<template>
  <!-- Dancing Letters Component -->
  <!-- Heavily inspired by https://codepen.io/jh3y/pen/OJMOmRL -->
  <h1
    class="message"
    :style="`--count: ${letters.length}; --duration: ${duration}s; --size: ${size}; --move: ${move}`"
  >
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
    duration: {
      type: String || Number,
      default: '2',
    },
    size: {
      type: String || Number,
      default: '1em',
    },
    move: {
      type: String || Number,
      default: '1em',
    },
  },
  computed: {
    letters() {
      return Array.from(this.text)
    },
  },
}
</script>
<style>
.message {
  font-size: var(--size);
  font-family: 'Roboto Mono', monospace;
  margin-bottom: var(--move);
}
.message span {
  display: inline-block;
  --hue: calc((360 / 7) * var(--index));
  color: hsl(var(--hue), 20%, 65%);
  font-variation-settings: 'wght' 200;
  transition: all 0.25s ease;
  animation: breathe var(--duration) infinite;
  animation-delay: calc(var(--duration) / var(--count) * var(--index));
  min-width: 0.25em;
}

.message span::after {
  content: attr(data-letter);
  display: block;
  position: absolute;
  top: 0.25em;
  left: 0.25em;
  opacity: 0.5;
  font-size: 0.75em;
}

@keyframes breathe {
  50% {
    font-variation-settings: 'wght' 700;
    color: hsl(var(--hue), 80%, 65%);
    transform: translateY(var(--move));
  }
}
</style>
