<template>
  <div id="personContent">
    <div id="" class="person-container">
      <div id="personContainer1" class="section person">
        <div class="bg-img"></div>
        <div class="first-part">
          <div class="pics column">
            <img src="../../assets/img/brand_pic1.png" alt="" />
          </div>
          <div class="column right">
            <h2 class="title">Join the B(r)and!</h2>
            <h3 class="subtitle">Partner With Auto-Tune</h3>

            <div class="info">
              <h5>
                Benefit from the global reach and influence that comes by
                partnering with Auto-Tune, one of the most recognized brand
                names in music.
              </h5>
              <ul>
                <li>
                  Auto-Tune is regularly covered by the global music,
                  entertainment, and technology press.
                </li>
                <li>
                  Auto-Tune redefined the way vocals are produced and is one of
                  the biggest selling plug-ins of all time.
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <div id="personContainer2" class="section person">
        <div class="bg-img"></div>
        <div class="first-part">
          <div class="column">
            <h2 class="title">Opportunities</h2>
            <h3 class="subtitle">Let's make lots of money</h3>

            <div class="info">
              <h5>
                By connecting the power of our brand with your community, the
                Auto-Tune affiliate program offers an easy way to earn.
              </h5>
              <ul>
                <li>
                  Generate extra income by helping your community solve the #1
                  problem seen in most music productions—vocal tuning.
                </li>
                <li>
                  Take advantage of generous payouts and a 30-day window for
                  your affiliate link to convert.
                </li>
              </ul>
            </div>
          </div>
          <div class="pics column">
            <img class="img-right" src="../../assets/img/income.png" alt="" />
          </div>
        </div>
      </div>
      <div id="personContainer3" class="section person">
        <div class="bg-img"></div>
        <div class="first-part">
          <div class="pics column">
            <img src="../../assets/img/brand_pic3.png" alt="" />
          </div>
          <div class="column right">
            <h2 class="title">Backstage Pass</h2>
            <h3 class="subtitle">In Da Club</h3>

            <div class="info">
              <h5>
                Auto-Tune Affiliates have preferred access to the Auto-Tune
                Marketing materials and an inside track to new product releases.
                You’ll hear it here first—and be able to turn that access into
                income.
              </h5>
              <ul>
                <li>
                  Enjoy access to marketing materials to help drive your
                  affiliate sales.
                </li>
                <li>Get prizes for your competitions and giveaways.</li>
                <li>Get all of the latest Antares software for FREE</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// GSAP Animation Imports
import { gsap, Power4 } from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  mounted() {
    this.setAnimationPerson();
  },
  methods: {
    setAnimationPerson() {
      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: "#personContainer1",
          scrub: 6,
          pin: "#personContent",
          start: "top top",
          end: "+=5000",
        },
      });
      tl.to(".bg-img", {
        backgroundPositionY: "170%",
        duration: 33,
      })
        .to(
          "#personContainer1 h2, #personContainer1 h3",
          {
            y: 0,
            opacity: 1,
            duration: 4,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer1 img",
          {
            x: 0,
            opacity: 0.95,
            duration: 3,
            ease: Power4.easeOut,
          },
          "<25%"
        )
        .to(
          "#personContainer1 h5",
          {
            opacity: 1,
            duration: 3,
            ease: Power4.easeOut,
          },
          "<25%"
        )
        .to(
          "#personContainer1 .info",
          {
            y: 0,
            duration: 1.5,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer1 li:nth-of-type(1)",
          {
            opacity: 1,
            x: 0,
            duration: 1,
            ease: Power4.easeOut,
          },
          "<30%"
        )
        .to(
          "#personContainer1 li:nth-of-type(2)",
          {
            opacity: 1,
            x: 0,
            duration: 1,
            ease: Power4.easeOut,
          },
          "<30%"
        )
        .to(
          "#personContainer1 img",
          {
            x: -100,
            opacity: 0,
            duration: 2,
            ease: Power4.easeOut,
          },
          ">2"
        )
        .to(
          "#personContainer1 h5",
          {
            opacity: 0,
            duration: 2,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer1 li",
          {
            opacity: 0,
            duration: 2,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer1 h2, #personContainer1 h3",
          {
            y: -50,
            opacity: 0,
            duration: 3,
            ease: Power4.easeOut,
          },
          ">"
        )
        .to(
          "#personContainer1",
          {
            display: "none",
            duration: 0.1,
            ease: Power4.easeOut,
          },
          ">"
        )
        .to(
          "#personContainer2",
          {
            display: "block",
            duration: 0.1,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer2 h2, #personContainer2 h3",
          {
            y: 0,
            opacity: 1,
            duration: 4,
            ease: Power4.easeOut,
          },
          ">"
        )
        .to(
          "#personContainer2 img",
          {
            x: 0,
            opacity: 0.95,
            duration: 3,
            ease: Power4.easeOut,
          },
          "<25%"
        )
        .to(
          "#personContainer2 h5",
          {
            opacity: 1,
            duration: 3,
            ease: Power4.easeOut,
          },
          "<25%"
        )
        .to(
          "#personContainer2 .info",
          {
            y: 0,
            duration: 1.5,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer2 li:nth-of-type(1)",
          {
            opacity: 1,
            ease: Power4.easeOut,
            x: 0,
            duration: 1,
          },
          "<30%"
        )
        .to(
          "#personContainer2 li:nth-of-type(2)",
          {
            opacity: 1,
            x: 0,
            duration: 1,
            ease: Power4.easeOut,
          },
          "<30%"
        )
        .to(
          "#personContainer2 img",
          {
            x: 100,
            opacity: 0,
            duration: 2,
            ease: Power4.easeOut,
          },
          ">2"
        )
        .to(
          "#personContainer2 h5",
          {
            opacity: 0,
            duration: 2,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer2 li",
          {
            opacity: 0,
            duration: 2,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer2 h2, #personContainer2 h3",
          {
            y: -50,
            opacity: 0,
            duration: 3,
            ease: Power4.easeOut,
          },
          ">"
        )
        .to(
          "#personContainer2",
          {
            display: "none",
            duration: 0.1,
            ease: Power4.easeOut,
          },
          ">"
        )
        .to(
          "#personContainer3",
          {
            display: "block",
            duration: 0.1,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer3 h2, #personContainer3 h3",
          {
            y: 0,
            opacity: 1,
            duration: 4,
            ease: Power4.easeOut,
          },
          ">"
        )
        .to(
          "#personContainer3 img",
          {
            x: 0,
            opacity: 0.95,
            duration: 3,
            ease: Power4.easeOut,
          },
          "<25%"
        )
        .to(
          "#personContainer3 h5",
          {
            opacity: 1,
            duration: 3,
            ease: Power4.easeOut,
          },
          "<25%"
        )
        .to(
          "#personContainer3 .info",
          {
            y: 0,
            duration: 1.5,
            ease: Power4.easeOut,
          },
          "<"
        )
        .to(
          "#personContainer3 li:nth-of-type(1)",
          {
            opacity: 1,
            ease: Power4.easeOut,
            x: 0,
            duration: 1,
          },
          "<30%"
        )
        .to(
          "#personContainer3 li:nth-of-type(2)",
          {
            opacity: 1,
            ease: Power4.easeOut,
            x: 0,
            duration: 1,
          },
          "<30%"
        )
        .to(
          "#personContainer3 li:last-of-type",
          {
            opacity: 1,
            x: 0,
            duration: 1,
            ease: Power4.easeOut,
          },
          "<30%"
        )

        .to(
          "#personContainer3 h5",
          {
            opacity: 0,
            duration: 6,
            ease: Power4.easeOut,
          },
          ">2"
        )
        .to(
          "#personContainer3 li",
          {
            opacity: 0,
            duration: 6,
            ease: Power4.easeOut,
          },
          "<"
        );
    },
  },
};
</script>

<style></style>
