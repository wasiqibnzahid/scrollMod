<template>
  <div>
    <!-- <div
      style="
        position: fixed;
        width: 200px;
        height: 200px;
        background: red;
        top: 50%;
        left: 50%;
        z-index: 20;
      "
    >
      {{ shownItem }}
    </div> -->
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
    const observer = new IntersectionObserver(
      (change) => {
        if (change[0].intersectionRatio >= 0.6) {
          if (this.firstItemTop == 0) {
            this.itemTop = change[0].rootBounds.height;
            this.firstItemTop = change[0].rootBounds.height;
          }

          window.addEventListener("scroll", () => {
            this.scrollFunctionFinal();
          });
        }
      },
      {
        threshold: 0.7,
      }
    );
    observer.observe(this.firstPerson);
  },
  unmounted() {
    window.removeEventListener("scroll", () => {
      this.scrollFunctionFinal();
    });
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
      scrollBasis: true,
      itemTop: 0,
      shownItem: 1,
      scrollDirection: "",
      firstItemTop: 0,
      runningScroll: false,
    };
  },
  methods: {
    scrollFunctionFinal() {
      var scroll = window.scrollY;
      setTimeout(() => {
        if (this.shownItem == 1) {
          this.$refs.personOne.$el.style.display = "block";
          this.$refs.personTwo.$el.style.display = "none";
          this.$refs.personThree.$el.style.display = "none";
        } else if (this.shownItem == 2) {
          this.$refs.personOne.$el.style.display = "none";
          this.$refs.personTwo.$el.style.display = "block";
          this.$refs.personThree.$el.style.display = "none";
        } else if (this.shownItem == 3) {
          this.$refs.personOne.$el.style.display = "none";
          this.$refs.personTwo.$el.style.display = "none";
          this.$refs.personThree.$el.style.display = "block";
        }
      }, 1000);
      if (this.runningScroll == true) {
        return;
      }
      this.runningScroll = true;
      if (scroll > this.firstItemTop) {
        this.lastPosition = scroll;
        if (scroll < this.firstItemTop + 4500) {
          this.shownItem = 1;
          this.itemTop = this.firstItemTop;
        } else if (
          scroll > this.firstItemTop + 4500 &&
          scroll < this.firstItemTop + 4500 + 4500
        ) {
          this.shownItem = 2;
          this.itemTop = this.firstItemTop + 4500;
        } else if (scroll > this.firstItemTop + 4500 + 4500) {
          this.shownItem = 3;
          this.itemTop = this.firstItemTop + 4500 + 4500;
        }
        if (scroll > this.itemTop && scroll < this.itemTop + 250) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "0";
            x.style.transform = "translateY(15rem)";
          });
          this.img.style.opacity = "0";
          if (this.shownItem != 2) {
            this.img.style.transform = "translateX(-12rem)";
          } else {
            this.img.style.transform = "translateX(12rem)";
          }
          this.miniHeading.style.opacity = "0";
          this.miniHeading.style.transform = "translateY(5rem)";
        } else if (scroll > this.itemTop + 50 && scroll < this.itemTop + 1000) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "0.2";
            x.style.transform = "translateY(12rem)";
            x.style.transition = "500ms";
          });
          this.miniHeading.style.transition = "500ms";
          this.img.style.transition = "500ms";
          this.list.forEach((x) => {
            x.style.transition = "500ms";
          });
          this.img.style.opacity = "0";
          if (this.shownItem != 2) {
            this.img.style.transform = "translateX(-12rem)";
          } else {
            this.img.style.transform = "translateX(12rem)";
          }
        } else if (
          scroll > this.itemTop + 1000 &&
          scroll < this.itemTop + 1100
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "0.4";
            x.style.transform = "translaetY(3rem)";
            x.style.transition = "";
          });
          this.miniHeading.style.transition = "";
          this.miniHeading.style.opacity = "0";
          this.miniHeading.style.transform = "translateY(5rem)";
          if (this.shownItem != 2) {
            this.img.style.transform = "translateX(-12rem)";
          } else {
            this.img.style.transform = "translateX(12rem)";
          }
          this.img.style.transition = "";
          this.list.forEach((x) => {
            x.style.transition = "";
          });
          this.img.style.opacity = "0";
        } else if (
          scroll > this.itemTop + 1000 &&
          scroll < this.itemTop + 1200
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "0.6";
            x.style.transform = "translateY(3rem)";
          });
          if (this.shownItem != 2) {
            this.img.style.transform = "translateX(-3rem)";
          } else {
            this.img.style.transform = "translateX(3rem)";
          }
          this.img.style.opacity = "0.5";
          this.miniHeading.style.opacity = "0";
          this.miniHeading.style.transform = "translateY(5rem)";
        } else if (
          scroll > this.itemTop + 1200 &&
          scroll < this.itemTop + 1300
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "0.8";
            x.style.transform = "translateY(1rem)";
          });
          this.img.style.opacity = "0.7";
          if (this.shownItem != 2) {
            this.img.style.transform = "translateX(-2rem)";
          } else {
            this.img.style.transform = "translateX(2rem)";
          }
          this.miniHeading.style.opacity = "0.4";
          this.miniHeading.style.transform = "translateY(3rem)";
        } else if (
          scroll > this.itemTop + 1300 &&
          scroll < this.itemTop + 1400
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "1";
            x.style.transform = "translateY(0rem)";
          });
          this.img.style.opacity = "0.95";
          this.img.style.transform = "translateX(0em)";
          this.miniHeading.style.opacity = "0.7";
          this.miniHeading.style.transform = "translateY(1rem)";
          this.list[0].style.opacity = "0";
          this.list[0].style.transform = "translate(4rem, 2rem)";
        } else if (
          scroll > this.itemTop + 1400 &&
          scroll < this.itemTop + 1500
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "1";
            x.style.transform = "translateY(0rem)";
          });
          this.miniHeading.style.opacity = "1";
          this.miniHeading.style.transform = "translateY(1rem)";
          this.list[0].style.opacity = "0.3";
          this.list[0].style.transform = "translate(2rem, 1rem)";
          this.list[1].style.opacity = "0";
          this.list[1].style.transform = "translate(4rem, 2rem)";
          this.img.style.opacity = "0.95";
          this.img.style.transform = "translateX(0em)";
        } else if (
          scroll > this.itemTop + 1500 &&
          scroll < this.itemTop + 1600
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "1";
            x.style.transform = "translateY(0rem)";
          });
          this.miniHeading.style.opacity = "1";
          this.miniHeading.style.transform = "translateY(0rem)";
          this.list[0].style.opacity = "0.5";
          this.list[0].style.transform = "translate(1rem, 0.75rem)";
          this.list[1].style.opacity = "0.3";
          this.list[1].style.transform = "translate(2rem, 1rem)";
          if (this.list[2]) {
            this.list[2].style.opacity = "0";
            this.list[2].style.transform = "translate(4rem, 2rem)";
          }
          this.img.style.opacity = "0.95";
          this.img.style.transform = "translateX(0em)";
        } else if (
          scroll > this.itemTop + 1700 &&
          scroll < this.itemTop + 1800
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "1";
            x.style.transform = "translateY(0rem)";
          });
          this.miniHeading.style.opacity = "1";
          this.miniHeading.style.transform = "translateY(0rem)";
          this.img.style.opacity = "0.95";
          this.img.style.transform = "translateX(0em)";
          this.list[0].style.opacity = "1";
          this.list[0].style.transform = "translate(0rem, 0rem)";
          this.list[1].style.opacity = "0.5";
          this.list[1].style.transform = "translate(1rem, 0.75rem)";
          if (this.list[2]) {
            this.list[2].style.opacity = "0.3";
            this.list[2].style.transform = "translate(2rem, 1rem)";
          }
        } else if (
          scroll > this.itemTop + 1800 &&
          scroll < this.itemTop + 1950
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "1";
            this.img.style.opacity = "0.95";
            this.img.style.transform = "translateX(0em)";
            x.style.transform = "translateY(0rem)";
          });
          this.miniHeading.style.opacity = "1";
          this.miniHeading.style.transform = "translateY(0rem)";
          this.list[0].style.opacity = "1";
          this.list[0].style.transform = "translate(0rem, 0rem)";
          this.list[1].style.opacity = "1";
          this.list[1].style.transform = "translate(0rem, 0rem)";
          if (this.list[2]) {
            this.list[2].style.transform = "translate(1rem, 0.75rem)";
          }
          this.img.style.opacity = "0.95";
          this.img.style.transform = "translateX(0em)";
        } else if (
          scroll > this.itemTop + 1950 &&
          scroll < this.itemTop + 2800
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "1";
            x.style.transform = "translateY(0rem)";
          });
          this.miniHeading.style.opacity = "1";
          this.miniHeading.style.transform = "translateY(0rem)";
          this.list[0].style.opacity = "1";
          this.list[1].style.opacity = "1";
          if (this.list[2]) {
            this.list[2].style.opacity = "1";
            this.list[2].style.transform = "translate(0,0)";
          }
          this.img.style.opacity = "0.95";
          this.img.style.transform = "translateX(0em)";
        } else if (
          scroll > this.itemTop + 2800 &&
          scroll < this.itemTop + 2900
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "1";
            x.style.transform = "translateY(0rem)";
          });
          this.miniHeading.style.opacity = "0.8";
          this.miniHeading.style.transform = "translateY(0rem)";
          this.list.forEach((x) => {
            x.style.opacity = 0.8;
          });
          this.img.opacity = "0.7";
          if (this.shownItem != 2) {
            this.img.transform = "translateX(-4rem)";
          } else {
            this.img.style.transform = "translateX(4rem)";
          }
        } else if (
          scroll > this.itemTop + 2900 &&
          scroll < this.itemTop + 3000
        ) {
          this.miniHeading.style.opacity = "0.5";
          this.list.forEach((x) => {
            x.style.opacity = "0.5";
          });
          this.img.opacity = "0.5";
          if (this.shownItem != 2) {
            this.img.transform = "translateX(-6rem)";
          } else {
            this.img.style.transform = "translateX(6rem)";
          }
        } else if (
          scroll > this.itemTop + 3000 &&
          scroll < this.itemTop + 3100
        ) {
          this.list.forEach((x) => {
            x.style.opacity = "0";
          });
          this.miniHeading.style.opacity = "0";
        } else if (
          scroll > this.itemTop + 3100 &&
          scroll < this.itemTop + 3200
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "1";
            x.style.transform = "translateY(0rem)";
          });
          this.miniHeading.style.opacity = "0";
          this.miniHeading.style.transform = "translateY(0rem)";
          this.img.style.opacity = "0";
          if (this.shownItem != 2) {
            this.img.style.transform = "translateX(-12rem)";
          } else {
            this.img.style.transform = "translateX(12rem)";
          }
        } else if (
          scroll > this.itemTop + 3200 &&
          scroll < this.itemTop + 3300
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "0.7";
            x.style.transform = "translateY(-2rem)";
          });
          this.miniHeading.style.opacity = "0";
          this.miniHeading.style.transform = "translateY(0rem)";
        } else if (
          scroll > this.itemTop + 3300 &&
          scroll < this.itemTop + 3400
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "0.4";
            x.style.transform = "translateY(-3.5rem)";
            x.style.transition = "";
          });
          this.miniHeading.style.opacity = "0";
          this.miniHeading.style.transition = "";
          this.miniHeading.style.transform = "translateY(0rem)";
          this.img.style.transition = "";
          this.list.forEach((x) => {
            x.style.transition = "";
          });
        } else if (
          scroll > this.itemTop + 3400 &&
          scroll < this.itemTop + 4500
        ) {
          this.firstHeadings.forEach((x) => {
            x.style.opacity = "0";
            x.style.transform = "translateY(-5rem)";
            x.style.transition = "500ms";
          });
          this.list.forEach((x) => {
            x.style.opacity = "0";
            x.style.transition = "500ms";
          });
          this.img.style.transition = "500ms";
          this.miniHeading.style.transition = "500ms";
          this.miniHeading.style.opacity = "0";
          this.miniHeading.style.transform = "translateY(0rem)";
        }
      }
      this.runningScroll = false;
    },
  },

  computed: {
    firstPerson() {
      var item;
      if (
        this.shownItem == 1 &&
        this.$refs.personOne &&
        this.$refs.personOne.$el
      ) {
        item = this.$refs.personOne.$el;
      } else if (
        this.shownItem == 2 &&
        this.$refs.personTwo &&
        this.$refs.personTwo.$el
      ) {
        item = this.$refs.personTwo.$el;
      } else if (
        this.shownItem == 3 &&
        this.$refs.personThree &&
        this.$refs.personThree.$el
      ) {
        item = this.$refs.personThree.$el;
      } else {
        item = "failed";
      }
      return item;
    },
    firstHeadings() {
      return this.firstPerson.querySelectorAll("h2, h3");
    },
    miniHeading() {
      return this.firstPerson.querySelector("h5");
    },
    list() {
      return this.firstPerson.querySelectorAll("li");
    },
    img() {
      return this.firstPerson.querySelector("img");
    },
  },
};
</script>
