<template>
  <div
    class="container topbar flex align-center"
    :class="addClass ? 'scrolled' : ''"
  >
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
    <div class="search flex align-center justify-end">
      <div class="img-container">
        <img
          style="width: 1.25rem"
          src="../../assets/img/search-icon.png"
          alt=""
        />
      </div>
      <div class="img-container">
        <img
          style="width: 1.75rem; margin-top: -5px; margin-left: -2px"
          src="../../assets/img/user-icon.png"
          alt=""
        />
      </div>
      <div class="img-container">
        <img
          style="width: 1.75rem; margin-left: -2px"
          src="../../assets/img/cart-icon.png"
          alt=""
        />
      </div>
    </div>
    <div class="button-container">
      <button>Apply Now!</button>
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
      addClass: false,
    };
  },
  methods: {
    setBackground() {
      if (window.scrollY > 50) {
        this.addClass = true;
      } else {
        this.addClass = false;
      }
    },
  },
  mounted() {
    window.addEventListener("scroll", this.setBackground);
  },
  unmounted() {
    window.removeEventListener("scroll", this.setBackground);

  }
};
</script>

<style></style>
