<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img :src="current" class="my-3" contain height="200" />
      </v-col>

      <v-row class="mb-4" justify="center" align-content="center">
        <v-img
          class="ma-4"
          v-for="(img, i) in gallery"
          :key="`pic-${i}`"
          max-height="100"
          max-width="100"
          :src="img.from"
          @click="clickGallery(img)"
        />
      </v-row>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref } from "vue";
const blank = require("../assets/blank.jpg")
const na = require("../assets/na.jpg");
const ni = require("../assets/ni.jpg");
const na_se = new Audio(require("../assets/se/na.mp3"));
const ni_se = new Audio(require("../assets/se/ni.mp3"));

const gallery = [
  { from: na, se: na_se },
  { from: ni, se: ni_se },
];
const current = ref(blank);
const ring = (se) => {
  se.currentTime = 0;
  se.play();
};
const clickGallery = (img) => {
  current.value = img.from;
  ring(img.se);
};
</script>
