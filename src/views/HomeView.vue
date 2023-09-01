<script setup lang="ts">
const audio = new Audio("audio/requiem.mp3");
audio.volume = 0.02;
audio.loop = true;

const play = () => audio.paused ? audio.play() : null;

</script>

<template>
  <main class="container">
    <p v-on:click="play" class="font-psych rainbow-trail" style="color: transparent; font-size: 10vw;">Magickal Execution</p>
  </main>
</template>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>

<style lang="scss">
$colors: #fff56d, #6ddaff, #ba6dff, #ff6dac;
$size: 20;

@mixin rainbow-shadow($colors, $offset: 0, $size: $size) {
  $len: length($colors);
  $outp: 0px 0px transparent;
  @for $i from 1 through $size {
    $ind: floor( max($i + $offset, 1) / $size * length($colors) ) % $len + 1;
    $col: nth($colors, $ind);
    $outp: #{$outp}, #{$i}px #{$i}px #{$col};
  }
  
  text-shadow: $outp;
}

.rainbow-trail {
  animation: animated-rainbow-shadow 1s infinite;
}

@keyframes animated-rainbow-shadow {
  @for $i from 0 to $size + 1 {
    #{$i / $size * 100}% {
      @include rainbow-shadow($colors, $i);
    }
  }
}
</style>