<template>
  <div>
    <Headers v-slot:header>{{ title }}</Headers>
    <div class="gallery">
      <div class="gallery-panel" v-for=" photo in photos" :key="photo.id">
        <nuxt-link :to="{name: 'Photo', query: { id: photo.id }}">
          <Gallery
            @click.native="() => updateSelected(photo.id)"
            :src="thumbUrl(photo.filename)"
            :alt="photo.alt"
            :title="photo.title"
          />
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import Gallery from "@/components/Gallery.vue";
import Headers from "@/components/Headers.vue";
import photos from "@/assets/data/gallery.json";

const mixin = {
  data() {
    return {
      selectedPhotoId: false
    };
  },
  methods: {
    // tracks and updates id as clicked- if not selected, border. if selected, unboarder.
    updateSelected: function(id) {
      this.selectedPhotoId = this.isSelected(id) ? undefined : id;
    },
    isSelected: function(id) {
      return this.selectedPhotoId == id;
    }
  }
};
export default {
  name: "Noms",
  components: {
    Gallery,
    Headers
  },

  mixins: [mixin],
  data() {
    return {
      photos,
      title: "Noms",
      tagLine: "What's cookin' good lookin'?"
    };
  },
  methods: {
    thumbUrl(filename) {
      return require(`../assets/img/gallery/thumbnails/${filename}`);
    }
  },
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

<style lang="scss" scoped>
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
  grid-gap: 1rem;
  max-width: 80rem;
  margin: 5rem auto;
  padding: 0 5rem;
}
.gallery-panel img {
  width: 100%;
  height: 22vw;
  object-fit: cover;
  border-radius: 0.75rem;
}
</style>
