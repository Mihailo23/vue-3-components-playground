<template>
  <div class="container text-center">
    <dancing-letters text="Mihailo je doktor" duration="2" size="80px" />
    <p>
      Inspiration:
      <a
        target="_blank"
        class="text-red-600"
        href="https://codepen.io/jh3y/pen/OJMOmRL"
        >this pen</a
      >
    </p>
  </div>
</template>

<script>
import DancingLetters from '@/components/DancingLetters'
export default {
  components: {
    DancingLetters,
  },
}
</script>

<style></style>
