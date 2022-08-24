<template>
  <div>
    <div class="home-container">
      <div class="user-img-container one"></div>
      <div class="user-img-container two"></div>
      <div class="bg-container-home"></div>
      <TopBar />
      <div class="home-content-box flex flex-column">
        <div class="home-content container">
          <h2>Why partner with Auto-Tune?</h2>
          <div class="flex align-center">
            <div class="down-arrow">&#8595;</div>
            <p>Scroll down and learn</p>
          </div>
        </div>
      </div>
    </div>
    <PersonContainer />
    <SubscriptionsSection />
    <PluginsSection />
    <FAQSection />
    <AffiliateSection />
  </div>
</template>

<script>
import TopBar from "../components/home/TopBar.vue";
import PersonContainer from "../components/home/PersonContainer.vue";
import PluginsSection from "../components/home/PluginsSection.vue";
import SubscriptionsSection from "../components/home/SubscriptionsSection.vue";
import AffiliateSection from "../components/home/AffiliateSection.vue";
import FAQSection from "../components/home/FAQSection.vue";

// GSAP Imports
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  mounted() {
    this.topBarAnimation();
  },
  methods: {
    topBarAnimation() {
      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: ".home-container",
          start: "top top",
          end: "bottom top",
          scrub: 8,
        },
      });
      tl.to(".user-img-container.one", {
        x: 600,
      }).to(
        ".user-img-container.two",
        {
          x: -600,
        },
        "<"
      );
    },
  },
  components: {
    TopBar,
    PersonContainer,
    SubscriptionsSection,
    PluginsSection,
    FAQSection,
    AffiliateSection,
  },
  data() {
    return {};
  },
};
</script>
