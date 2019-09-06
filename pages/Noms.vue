<template>
  <div>
    <Headers v-slot:header>{{ title }}</Headers>
    <Gallery />
  </div>
</template>

<script>
import Gallery from "@/components/Gallery.vue";
import Headers from "@/components/Headers.vue";

export default {
  name: "Noms",
  components: {
    Gallery,
    Headers
  },
  data: () => ({
    title: "Noms",
    tagLine: "What's cookin' good lookin'?"
  }),
  head() {
    return {
      title: this.title,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: "description",
          name: "description",
          content: "My custom description"
        }
      ]
    };
  }
};
</script>
