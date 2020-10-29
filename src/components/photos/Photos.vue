<template>
  <div class="photos">
    <Nasa
      v-for="nasaPhoto of nasaPhotos"
      v-bind:key="nasaPhoto.id"
      v-bind:nasaPhoto="nasaPhoto"
    />

    <Unsplash
      v-for="unsplashPhoto of unsplashPhotos"
      v-bind:unsplashPhoto="unsplashPhoto"
      v-bind:key="unsplashPhoto.id"
    />
  </div>
</template>

<script>
import Nasa from "@/components/photo/Nasa";
import Unsplash from "@/components/photo/Unsplash";

export default {
  props: {
    nasaPhotos: {
      type: Array,
    },
    unsplashPhotos: {
      type: Array,
    },
  },
  components: {
    Nasa,
    Unsplash,
  },
  methods: {},
};
</script>

<style scoped>
.photos {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(auto, 1fr);
  grid-column-gap: 1rem;
  grid-row-gap: 1rem;
}
</style>