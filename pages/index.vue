<template>
  <div class="container">
    <dancing-letters text="Mihailo" />
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

<style>
/* Sample `apply` at-rules with Tailwind CSS
*/
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
</style>
