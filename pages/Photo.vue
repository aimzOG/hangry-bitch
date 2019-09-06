<template>
  <div class="photo">
    <!-- <h1 class="display-2 text-sm-center text-lg-right">{{title}}</h1> -->
    <Gallery />
    <Lightbox />
  </div>
</template>

<script>
import Gallery from "@/components/Gallery.vue";
import Lightbox from "@/components/Lightbox.vue";

export default {
  name: "Photo",
  components: {
    Gallery,
    Lightbox
  },
  data: () => ({
    title: "Recipe"
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
