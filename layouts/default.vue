<template>
  <div>
    <Nav />
    <nuxt />
  </div>
</template>

<script>
// imports nav only once
import Nav from "@/components/Nav.vue";

export default {
  name: "default",
  components: {
    Nav
  }
};
</script>

<style>
</style>
