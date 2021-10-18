<template>
  <div class="w-full flex justify-center py-3 bg-purple-900">
    <h1 class="text-xl text-white font-bold">TIC TAC TOE</h1>
  </div>
  <div class="w-full flex justify-around py-3 bg-dark-100">
    <Difficulty />
  </div>
</template>
<script>
import Difficulty from "./options/Difficulty.vue";
export default {
  components: {
    Difficulty,
  },
};
</script>

<style>
</style>