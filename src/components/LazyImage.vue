<template>
  <intersect @enter.once="onEnter">
    <div class="relative">
      <!-- Show the placeholder as background -->
      <blurhash-img
        :hash="blurhash"
        :aspect-ratio="height / width"
        class="absolute top-0 left-0 transition-opacity duration-500"
        :class="isLoaded ? 'opacity-0' : 'opacity-100'"
      />

      <!-- Show the real image on the top and fade in after loading -->
      <img
        ref="image"
        :width="width"
        :height="height"
        v-bind="$attrs"
        class="absolute top-0 left-0 transition-opacity duration-500"
        :class="isLoaded ? 'opacity-100' : 'opacity-0'"
      >
    </div>
  </intersect>
</template>

<script>
import BlurhashImg from "./BlurhashImg";
import Intersect from "vue-intersect";

export default {
  components: {
    Intersect,
    BlurhashImg
  },

  inheritAttrs: false,

  props: {
    src: {
      type: String,
      required: true
    },
    blurhash: {
      type: String,
      required: false,
      default: null
    },
    width: {
      type: Number,
      default: 1
    },
    height: {
      type: Number,
      default: 1
    }
  },

  data() {
    return {
      isVisible: false,
      isLoaded: false
    };
  },

  methods: {
    onEnter() {
      // Image is visible (means: has entered the viewport),
      // so start loading by setting the src attribute
      this.$refs.image.src = this.src;

      this.$refs.image.onload = () => {
        // Image is loaded, so start fading in

        // Just for this demo: Wait a second, so the BlurHash
        // is visible a little longer
        setTimeout(() => {
          this.isLoaded = true;
        }, 1000);
      };
    }
  }
};
</script>
