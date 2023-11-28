<script setup lang="ts">
interface Props {
  text: string;
  textSize: string;
}

const props = defineProps<Props>();
</script>

<template>
  <div
    :style="{ fontSize: props.textSize, color: 'white' }"
    class="rainbow-trail font-psych"
  >{{ props.text }}</div>
</template>

<style lang="scss">
$colors: #fff56d, #6ddaff, #ba6dff, #ff6dac;
$size: 30;

@mixin rainbow-shadow($colors, $offset: 0, $size: $size) {
  $len: length($colors);
  $outp: 0px 0px transparent;
  @for $i from 1 through $size {
    $ind: floor(calc(max($i + $offset, 1) / $size) * length($colors)) % $len + 1;
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
    #{calc($i / $size) * 100}% {
      @include rainbow-shadow($colors, $i);
    }
  }
}
</style>