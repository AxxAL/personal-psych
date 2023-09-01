<script lang="ts">
import { RouterView } from "vue-router";
import { defineComponent } from "vue";

export default defineComponent({
  components: {
    RouterView
  }
});
</script>

<template>
  <main class="wrapper">
    <RouterView />
  </main>
</template>

<style scoped>

</style>
