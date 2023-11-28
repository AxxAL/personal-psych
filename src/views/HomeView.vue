<script setup lang="ts">
import PsychText from "../components/PsychText.vue";
import { ref } from "vue";

const mouseX = ref(0);
const mouseY = ref(0);

function onMouseMove(event: MouseEvent) {
  mouseX.value = event.clientX;
  mouseY.value = event.clientY;
}
</script>

<template>
  <main
    class="container"
    @mousemove="onMouseMove"
    :style="{ backgroundColor: `hsl(${(mouseX + mouseY) / 10}, 80%, 50%)` }"
  >
    <PsychText text="Magickal Execution" text-size="10vw" />
  </main>
</template>

<style lang="scss">
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>