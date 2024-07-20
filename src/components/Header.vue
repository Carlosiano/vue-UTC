<script setup>
import { arrowForwardOutline, closeOutline, logoNav, menuOutline, personAddOutline } from "../assets/images";
import { navLinks } from "../assets/js/data";
</script>

<script>
export default {
  data() {
    return {
      isActive: false
    };
  },
  props: {
    scrollY
  },
}
</script>

<template>
  <header class="header" :class="{ active: scrollY > 100 }" data-header>
    <div class="container">
      <a href="#" class="logo">
        <img :src="logoNav" alt="UTC logo" />
      </a>

      <nav class="navbar" data-navbar :class="{ active: isActive }">
        <div class="wrapper">
          <a href="#" class="logo">
            <img :src="logoNav" width="162" height="50" alt="UTC logo" />
          </a>

          <button class="nav-close-btn" aria-label="close menu" data-nav-toggler @click="isActive = !isActive">
            <div class="ion-icon" :style="{ 'mask-image': `url(${closeOutline})` }" aria-hidden="true"></div>
          </button>
        </div>
        <ul class="navbar-list">
          <li class="navbar-item" v-for="(item, index) in navLinks" :key="index" @click="isActive = !isActive">
            <a :href="`#${item.href}`" class="navbar-link" data-nav-link>{{ item.title }}</a>
          </li>
        </ul>
      </nav>

      <div class="header-actions">
        <a href="#" class="btn has-before">
          <div class="ion-icon" :style="{ 'mask-image': `url(${personAddOutline})` }" aria-hidden="true"></div>
          <span class="span">Daftar</span>
        </a>
        <a href="#" class="btn-second has-before">

          <div class="ion-icon" :style="{ 'mask-image': `url(${arrowForwardOutline})` }" aria-hidden="true"></div>
          <span class="span">Masuk</span>
        </a>

        <button class="header-action-btn" aria-label="open menu" data-nav-toggler @click="isActive = !isActive">
          <div class="ion-icon" :style="{ 'mask-image': `url(${menuOutline})` }" aria-hidden="true"></div>
        </button>
      </div>

      <div class="overlay" data-nav-toggler data-overlay :class="{ active: isActive }" @click="isActive = !isActive">
      </div>
    </div>
  </header>

</template>
