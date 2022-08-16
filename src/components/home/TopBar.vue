<template>
  <div class="container topbar flex align-center">
    <div class="flex align-center">
      <div class="img-container">
        <img src="../../assets/img/threedots.png" alt="" />
      </div>
      <h4 class="text-white">AUTO-TUNE</h4>
    </div>
    <nav class="flex align-center">
      <router-link v-for="(item, index) in navLinks" :key="index" :to="item.to">
        {{ item.text }}
      </router-link>
    </nav>
    <div class="search flex align-center justify-center">
      <div class="img-container">
        <img src="../../assets/img/threedots.png" alt="" />
      </div>
      <div class="img-container">
        <img src="../../assets/img/threedots.png" alt="" />
      </div>
      <div class="img-container">
        <img src="../../assets/img/threedots.png" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      navLinks: [
        { text: "Home", to: "/" },
        { text: "Products", to: "/" },
        { text: "Learning Center", to: "/" },
        { text: "Community", to: "/" },
        { text: "Support", to: "/" },
      ],
    };
  },
};
</script>

<style></style>
