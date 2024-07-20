<script setup>
import { chevronUp } from './assets/images';
import { Header, Main, Footer } from './components';
</script>

<script>
export default {
  name: "App",
  data() {
    return {
      scrollY: 0
    };
  },
  mounted() {
    window.addEventListener("scroll", this.onScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    onScroll(e) {
      this.scrollY = e.target.documentElement.scrollTop;
      // console.log({ top: this.scrollY });
    }
  }
};
</script>

<template>
  <Header :scrollY="scrollY" />
  <Main />
  <Footer />

  <!-- 
    - #BACK TO TOP
  -->

  <a href="#top" class="back-top-btn" :class="{ active: scrollY > 100 }" aria-label="back top top" data-back-top-btn>
    <div class="ion-icon" :style="{ 'mask-image': `url(${chevronUp})` }" aria-hidden="true"></div>
  </a>

</template>
