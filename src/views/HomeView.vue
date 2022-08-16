<template>
  <div>
    <div class="home-container">
      <div class="user-img-container"></div>
      <div class="bg-container-home"></div>
      <div class="home-content-box flex flex-column">
        <TopBar />
        <div class="home-content container">
          <h2>Why partner with Auto-Tune?</h2>
          <div class="flex align-center">
            <div class="down-arrow">&#8595;</div>
            <p>Scroll down and learn</p>
          </div>
        </div>
      </div>
    </div>
    <firstPerson />
    <secondPerson />
    <thirdPerson />
    <SubscriptionsSection />
    <PluginsSection />
    <FAQSection />
    <AffiliateSection />
  </div>
</template>

<script>
import TopBar from "../components/home/TopBar.vue";
import firstPerson from "../components/home/firstPerson.vue";
import secondPerson from "../components/home/secondPerson.vue";
import thirdPerson from "../components/home/thirdPerson.vue";
import PluginsSection from "../components/home/PluginsSection.vue";
import SubscriptionsSection from "../components/home/SubscriptionsSection.vue";
import AffiliateSection from "../components/home/AffiliateSection.vue";
import FAQSection from "../components/home/FAQSection.vue";
export default {
  components: {
    TopBar,
    firstPerson,
    secondPerson,
    thirdPerson,
    SubscriptionsSection,
    PluginsSection,
    FAQSection,
    AffiliateSection,
  },
  mounted() {},
  data() {
    return {
      lastPosition: 0,
      showMyItem: true,
    };
  },
  methods: {},
};
</script>
