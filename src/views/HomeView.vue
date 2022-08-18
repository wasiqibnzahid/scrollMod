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
  unmounted() {
    window.removeEventListener('scroll', this.scrollFunction)
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
    };
  },
  methods: {
    scrollFunction() {
      console.log(window.scrollY);
      const innerInfo = this.$refs.personOne.$el.querySelectorAll("h2, h3");
      const miniHeading = this.$refs.personOne.$el.querySelector("h5");
      const list = this.$refs.personOne.$el.querySelectorAll("li");
      const person = this.$refs.personOne.$el.querySelector("img");

      if (window.scrollY >= 915) {
        if (this.lastPosition < 915) {
          this.lastPosition = window.scrollY;
        } else if (this.lastPosition + 20 <= window.scrollY) {
          this.$refs.personOne.$el.querySelector(".bg-img").style.top = `${
            parseFloat(
              this.$refs.personOne.$el
                .querySelector(".bg-img")
                .style.top.replace("rem", "")
            ) - 0.1
          }rem`;
          this.lastPosition = window.scrollY;
          if (window.scrollY > 915 && window.scrollY < 1250) {
            innerInfo.forEach((x) => {
              var translate = parseInt(
                x.style.transform.replaceAll(/^\D+/g, "")
              );
              if (parseFloat(x.style.opacity) < 1 && this.scrollBasis) {
                x.style.opacity = `${parseFloat(x.style.opacity) + 0.25}`;
              } else if (x.style.opacity == "") {
                x.style.opacity = "0";
              }
              if (translate > 0 && this.scrollBasis) {
                x.style.transform = `translateY(${translate - 4}rem)`;
              } else if (x.style.transform == "") {
                x.style.transform = "translateY(16rem)";
              }
            });
            if (window.scrollY > 980) {
              if (person.style.opacity != "" && person.style.opacity < 0.9) {
                person.style.opacity = `${
                  parseFloat(person.style.opacity) + 0.24
                }`;
                console.log(
                  parseInt(person.style.transform.replaceAll(/^\D+/g, ""))
                );
                person.style.transform = `translateX(-${
                  parseFloat(person.style.transform.replaceAll(/^\D+/g, "")) - 3
                }rem)`;
              } else if (person.style.opacity == "") {
                person.style.opacity = "0";
                person.style.transform = "translateX(-12rem)";
              }
            }
            if (window.scrollY > 1021) {
              if (miniHeading.style.transform == "") {
                miniHeading.style.transform = "translateY(9rem)";
              }
              if (miniHeading.style.opacity == "") {
                miniHeading.style.opacity = "0";
              } else if (miniHeading.style.opacity < 1) {
                var translate = parseInt(
                  miniHeading.style.transform.replaceAll(/^\D+/g, "")
                );
                miniHeading.style.opacity = `${
                  parseFloat(miniHeading.style.opacity) + 0.34
                }`;
                miniHeading.style.transform = `translateY(${translate - 3}rem)`;
              }
            }
            if (window.scrollY > 1045) {
              if (list[0].style.opacity == "") {
                list.forEach((x) => {
                  x.style.marginLeft = "1rem";
                  x.style.transform = "translateY(2rem)";
                  x.style.opacity = "0";
                });
              } else if (list[0].style.opacity < 1) {
                list[0].style.transform = `translateY(${
                  parseFloat(list[0].style.transform.replaceAll(/^\D+/g, "")) -
                  0.5
                }rem)`;
                list[0].style.opacity = `${
                  parseFloat(list[0].style.opacity) + 0.25
                }`;
                list[0].style.marginLeft = `${
                  parseFloat(list[0].style.marginLeft.replace("rem", "")) - 0.25
                }rem`;
              }
            }
            if (window.scrollY > 1109) {
              if (list[1].style.opacity < 1) {
                list[1].style.transform = `translateY(${
                  parseFloat(list[1].style.transform.replaceAll(/^\D+/g, "")) -
                  0.5
                }rem)`;
                list[1].style.opacity = `${
                  parseFloat(list[1].style.opacity) + 0.25
                }`;
                list[1].style.marginLeft = `${
                  parseFloat(list[1].style.marginLeft.replace("rem", "")) - 0.25
                }rem`;
              }
            }
          }
          if (window.scrollY > 1450) {
            if (window.scrollY > 1650) {
              innerInfo.forEach((x) => {
                if (x.style.opacity > 0) {
                  x.style.opacity = `${parseFloat(x.style.opacity) - 0.35}`;
                }
                 var translate = parseInt(
                x.style.transform.replaceAll(/^\D+/g, "")
              );

                if (translate < 16) {
                  x.style.transform = `translateY(-${translate + 1}rem)`;
                }
              });
              if (window.scrollY > 1520) {
                if (person.style.opacity != "" && person.style.opacity > 0) {
                  person.style.opacity = `${
                    parseFloat(person.style.opacity) - 0.24
                  }`;
                  person.style.transform = `translateX(-${
                    parseFloat(person.style.transform.replaceAll(/^\D+/g, "")) +
                    3
                  }rem)`;
                }

              }
            }
            miniHeading.style.opacity = parseFloat(miniHeading.style.opacity)
            // if (window.scrollY > 1640) {
            //   if (miniHeading.style.opacity > 0) {
            //     miniHeading.style.opacity = `${
            //       parseFloat(miniHeading.style.opacity) - 0.34
            //     }`;
            //     miniHeading.style.transform = `translateY(${translate + 3}rem)`;
            //   }
            // }
            // if (window.scrollY > 1495) {
            //   if (list[1].style.opacity > 0) {
            //     list[1].style.transform = `translateY(${
            //       parseFloat(list[1].style.transform.replaceAll(/^\D+/g, "")) +
            //       0.5
            //     }rem)`;
            //     list[1].style.opacity = `${
            //       parseFloat(list[1].style.opacity) - 0.25
            //     }`;
            //     list[1].style.marginLeft = `${
            //       parseFloat(list[1].style.marginLeft.replace("rem", "")) + 0.25
            //     }rem`;
            //   }
            // }
            // if (window.scrollY > 1644) {
            //   if (list[0].style.opacity > 0) {
            //     list[0].style.transform = `translateY(${
            //       parseFloat(list[0].style.transform.replaceAll(/^\D+/g, "")) +
            //       0.5
            //     }rem)`;
            //     list[0].style.opacity = `${
            //       parseFloat(list[0].style.opacity) - 0.25
            //     }`;
            //     list[0].style.marginLeft = `${
            //       parseFloat(list[0].style.marginLeft.replace("rem", "")) + 0.25
            //     }rem`;
            //   }
            // }
          }
        } else if (this.lastPosition - 20 >= window.scrollY) {
          this.$refs.personOne.$el.querySelector(".bg-img").style.top = `${
            parseFloat(
              this.$refs.personOne.$el
                .querySelector(".bg-img")
                .style.top.replace("rem", "")
            ) + 0.1
          }rem`;
          this.lastPosition = window.scrollY;
          innerInfo.forEach((x) => {
            if (x.style.opacity != "" && x.style.opacity > 0) {
              x.style.opacity = `${parseFloat(x.style.opacity) - 0.25}`;
              var translate = parseInt(
                x.style.transform.replaceAll(/^\D+/g, "")
              );
              if (translate < 25) {
                // x.style.transform = `translateY(${translate + 4}rem)`;
              }
            }
          });
        }
        // console.log(window.scrollY, 1120, 1320)
      } else if (window.scrollY < 915) {
        innerInfo.forEach((x) => {
          x.style.opacity = "0";
          x.style.transform = "translateY(16rem)";
        });
        list.forEach((x) => {
          x.style.opacity = "0";
          x.style.transform = "translateY(2rem)";
          x.style.marginLeft = "2rem";
        });
        miniHeading.style.opacity = "0";
        miniHeading.style.transform = "translateY(2rem)";
        person.style.opacity = "0";
        person.style.transform = "translateX(-12rem)";
      }
    },
  },
};
</script>
