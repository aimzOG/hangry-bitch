<template>
  <!-- uses props to render title src and alt -->
  <img v-bind:title="title" :src="src" :alt="alt" />
</template>

<script>
export default {
  name: "Gallery",
  // prop validation
  props: {
    src: String,
    alt: String,
    title: String
  }
};
</script>
