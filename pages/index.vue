<template>
  <div class="hello">
    <Headers v-slot:header>{{ title }}</Headers>
    <b-carousel
      id="carousel-fade"
      style="text-shadow: 0px 0px 2px #000"
      fade
      indicators
      controls
      img-width="1024"
      img-height="480"
    >
      <b-carousel-slide
        v-for="image in carousel"
        :key="image.src"
        :caption="image.caption"
        :text="image.text"
        :img-src="image.src"
      />
    </b-carousel>
    <!-- jumbotron -->
    <div class="jumbotron">
      <h1 class="display-4">{{ jumbotron.title }}</h1>
      <p class="lead" />
      <hr class="my-4" />
      <p>{{ jumbotron.text }}</p>
      <p class="lead">
        <!-- includes tool tip -->
        <a
          class="btn btn-primary btn-lg"
          href="#"
          role="button"
          data-toggle="tooltip"
          data-placement="bottom"
          title="Click to go to submission page"
        >
          Submit My
          Recipe!
        </a>
      </p>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Headers from "@/components/Headers.vue";
import homeCutlery from "@/assets/img/home-cutlery.jpg";
import homeFood from "@/assets/img/home-food.jpg";
import homeDrink from "@/assets/img/home-drink.jpg";

export default {
  name: "Home",
  components: {
    Headers
  },
  data: () => ({
    title: "Hangry Bitch.",
    jumbotron: {
      title: "Get featured on Hangry Bitch!",
      text:
        "Have a delicious creation you'd like to share? Submit your recipe and a picture using the button below and we'll feature your concotion on our site!"
    },
    carousel: [
      {
        src: homeCutlery,
        caption: "",
        text: "",
        position: ""
      },
      {
        src: homeFood,
        caption: "Noms",
        text: "Food is love, love is food",
        position: "text-left"
      },
      {
        src: homeDrink,
        caption: "Sippin's",
        text: "Good for the soul",
        position: "text-right"
      }
    ]
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

<style>
</style>
