<template>
  <!-- enlarges selected picture and shows attached info -->
  <div class="lightbox">
    <div class="lightbox-info">
      <button class="exit_button" @click.self="closeLightbox">X</button>
      <!-- if json holds this data, show when lightbox is activated -->
      <div class="lightbox-info-inner">
        <div class="food-heading text-center">
          <h2 class="display 2" v-if="photo.title">{{ photo.title }}</h2>
          <h3 class="text-muted" v-if="photo.chef">
            <a rel="nofollow" :href="photo.chef.url">{{ photo.chef.name }}</a>
          </h3>
          <p v-if="photo.source">
            <a rel="nofollow" :href="photo.source.url">{{ photo.source.name }}</a>
          </p>
        </div>
        <div class="recipe" v-if="photo.recipe">
          <div class="recipe__preview">
            <Gallery
              :src="photoUrl(photo.filename)"
              :alt="photo.alt"
              :title="photo.title"
              class="recipe__preview__img"
            />
          </div>
          <div class="recipe__directions">
            <section class="recipe__ingredients">
              <h4>Ingredients</h4>
              <ul class="ingredient__list">
                <li
                  class="ingredient__list__item"
                  v-for="(ingredient, ingredients) in photo.recipe.ingredients"
                  :key="ingredients"
                >{{ ingredient }}</li>
              </ul>
            </section>
            <section class="recipe__instructions">
              <h4>Recipe</h4>
              <ol class="instruction__list">
                <li
                  class="instruction__list__item"
                  v-for="(instruction, instructions) in photo.recipe.instructions"
                  :key="instructions"
                >{{ instruction }}</li>
              </ol>
            </section>
          </div>
          <Nutrition />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Gallery from "@/components/Gallery.vue";
import photos from "@/assets/data/gallery.json";
import Nutrition from "@/components/Nutrition.vue";

export default {
  name: "Lightbox",
  components: {
    Gallery,
    Nutrition
  },

  data() {
    return {
      photos
    };
  },
  computed: {
    photo() {
      return this.photos.find(photo => {
        return photo.id === Number(this.$route.query.id);
      });
    }
  },
  methods: {
    photoUrl(filename) {
      return require(`../assets/img/${filename}`);
    },
    closeLightbox() {
      this.$router.push("/noms");
    }
  }
};
</script>

<style lang="scss">
@import "@/assets/styles/main.scss";

.lightbox {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
  overflow-x: scroll;

  h1,
  h2,
  h4,
  h5 {
    font-family: "Permanent Marker";
  }
}

.lightbox-info {
  margin: 0 auto;
  padding: 2rem;
  max-width: 1200px;
}

.exit_button {
  float: right;
  font-weight: bold;
  background: transparent;
  border: 1px solid white;
  border-radius: 50%;
  &:hover {
    background-color: grey;
  }
}
.recipe__directions {
  display: flex;
  flex-direction: column;
  margin-bottom: 2rem;

  @include media-query(lg) {
    flex-direction: row;
    justify-content: space-around;
  }
}

.recipe__preview {
  margin-bottom: 2rem;
  &__img {
    max-width: 100%;
  }
}

.instruction__list {
  list-style: none;
  counter-reset: item;

  &__item {
    counter-increment: item;
    margin-bottom: 5px;

    &:before {
      margin-right: 10px;
      content: counter(item);
      background: #0069d9;
      border-radius: 100%;
      color: white;
      width: 1.2em;
      text-align: center;
      display: inline-block;
    }
  }
}
</style>
