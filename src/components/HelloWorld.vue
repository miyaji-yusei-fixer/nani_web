<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img :src="current" class="my-3" contain height="200" />
      </v-col>

      <v-col>
        <v-row
          v-for="(row, i) in gallery"
          :key="`row-${i}`"
          justify="center"
          align-content="center"
        >
          <v-img
            class="ma-4"
            v-for="(img, j) in row"
            :key="`pic-${j}`"
            max-height="100"
            max-width="100"
            :src="img.from"
            @click="clickGallery(img)"
          />
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref } from "vue";
const blank = require("../assets/blank.jpg");
const na = require("../assets/na.jpg");
const ni = require("../assets/ni.jpg");
const hi = require("../assets/hi.jpg");
const itandesuyo = require("../assets/itandesuyo.jpg");
const na_se = new Audio(require("../assets/se/na.mp3"));
const ni_se = new Audio(require("../assets/se/ni.mp3"));
const hi_se = new Audio(require("../assets/se/hi.mp3"));
const itandesuyo_se = new Audio(require("../assets/se/itandesuyo.mp3"));

const gallery = [
  [
    { from: na, se: na_se },
    { from: ni, se: ni_se },
  ],
  [
    { from: hi, se: hi_se },
    { from: itandesuyo, se: itandesuyo_se },
  ],
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
