<template>
  <div class="p-5 max-w-4xl mx-auto">
    <h1 class="my-2 text-3xl">Progressive image loading with BlurHash</h1>

    <p>
      Example using Vue.js 3. Full article here:
      <br />
      <a
        class="underline"
        href="https://ledermann.dev/blog/2020/08/01/progressive-image-loading-with-blurhash/">
        <strong>ledermann.dev</strong
        >/blog/2020/08/01/progressive-image-loading-with-blurhash
      </a>
    </p>

    <lazy-image
      class="my-10"
      :src="image1"
      blurhash="LlNA}44TN{kqyEtls:xux^tRRjRi"
      :width="3872"
      :height="2592" />

    <lazy-image
      class="my-10"
      :src="image2"
      blurhash="LhEq+[~ntkV[HCNHo0jFTJR6V[kC"
      :width="1814"
      :height="3225" />

    <lazy-image
      class="my-10"
      :src="image3"
      blurhash="LDE.CU9FaKR*?wM{ayay00%ff+oe"
      :width="5304"
      :height="7952" />

    <lazy-image
      class="my-10"
      :src="image4"
      blurhash="LUDdt:M{ysf7J:ofR4j[S5ayVsay"
      :width="4008"
      :height="5013" />
  </div>
</template>

<script>
import image1 from '@/assets/images/photo-1451153378752-16ef2b36ad05.jpeg';
import image2 from '@/assets/images/photo-1579419964575-8c5d90b6522b.jpeg';
import image3 from '@/assets/images/photo-1541336032412-2048a678540d.jpeg';
import image4 from '@/assets/images/photo-1551128997-c2b66772f982.jpeg';
import LazyImage from '@/components/LazyImage.vue';

export default {
  name: 'App',

  components: {
    LazyImage,
  },

  data() {
    return {
      image1,
      image2,
      image3,
      image4,
    };
  },
};
</script>
