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
    <div ref="person-container" class="person-container">
      <firstPerson class="firstPerson" ref="personOne" />
      <secondPerson class="secondPerson" ref="personTwo" />
      <thirdPerson class="thirdPerson" ref="personThree" />
    </div>
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
  mounted() {
    window.addEventListener("scroll", this.scrollFunction);
  },
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
  data() {
    return {
      lastPosition: 0,
      showMyItem: true,
    };
  },
  methods: {
    scrollFunction() {
      var innerInfo = this.$refs.personOne.$el.querySelectorAll("h2, h3");
      if (window.scrollY >= 1007) {
        if (this.lastPosition < 1007) {
          this.lastPosition = window.scrollY;
        } else if (this.lastPosition + 15 <= window.scrollY) {
          this.lastPosition = window.scrollY;
          innerInfo.forEach((x) => {
            if (x.style.opacity != "" && parseInt(x.style.opacity) < 1) {
              var translate = parseInt(x.style.transform.replaceAll(/^\D+/g, "").replace("%)", ""))
              x.style.opacity = `${parseFloat(x.style.opacity) + 0.1}`;
              if(translate > 0) {
                x.style.transform = `translateX(${translate - 4}%)`
                console.log(x.style.transform)
              }
              
            } else if (x.style.opacity == "") {
              x.style.opacity = "0";
              x.style.transform = "translateX(20%)";
            }
          });
        } else if (this.lastPosition - 15 >= window.scrollY) {
          this.lastPosition = window.scrollY;
          innerInfo.forEach((x) => {
            if (x.style.opacity != "" && parseFloat(x.style.opacity) > 0) {
              x.style.opacity = `${parseFloat(x.style.opacity) - 0.1}`;
               var translate = parseInt(x.style.transform.replaceAll(/^\D+/g, "").replace("%)", ""))
               if(translate < 20) {
                x.style.transform = `translateX(${translate + 4}%)`

               }
            }
          });
        }
        // console.log(window.scrollY, 1120, 1320)
      }
    },
  },
};
</script>
