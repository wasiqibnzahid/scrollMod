<template>
  <div class="container subscription">
    <div class="section">
      <h4>HOW AFFILIATES GET PAID</h4>
      <h2>Auto-Tune Unlimited Subscriptions</h2>
      <p>
        Affiliates are paid flat rates for initial Auto-Tune Unlimited
        subscription sales when purchased via affiliate links. In USD that comes
        out to:
      </p>
      <div class="price" ref="priceContainer">
        <div class="detail one">
          <div class="price-detail"><span>$</span>5</div>
          <div class="description">
            for each Auto-Tune Unlimited Monthly Subscription Trial
          </div>
        </div>
        <div class="detail two">
          <div class="price-detail"><span>$</span>30</div>
          <div class="description">
            for each paid Auto-Tune Unlimited Monthly Subscription sold for
            $24.99
          </div>
        </div>
        <div class="detail three">
          <div class="price-detail"><span>$</span>45</div>
          <div class="description">
            for each paid Auto-Tune Unlimited Monthly Subscription sold for
            $174.99
          </div>
        </div>
      </div>
      <div class="learn-more">
        <p>
          <a href="#">LEARN MORE ABOUT AUTO-TUNE UNLIMITED</a>
        </p>
      </div>
      <h2>Perpetual Plugins</h2>
      <div ref="tierContainer" class="tiers">
        <div class="tier one">
          <div class="head">Tier 1</div>
          <p>
            For each sale of any perpetual plug-in license, affiliates are paid
            10% of the price listed on our website. This includes licenses for
            every edition of Auto-Tune and every vocal effect sold on our
            website.
          </p>
          <p class="tier-note">(Note that it does not include upgrades.)</p>
        </div>
        <div class="tier two">
          <div class="head">Tier 2</div>
          <p>
            If an affiliate generates $2,000 or more of sales per month, they
            are paid 20% of the price seen on our website.
          </p>
          <p class="tier-note">(Note that it does not include upgrades.)</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// GSAP Animation imports
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  data() {
    return {
      itemTop: 0,
      tierTop: 0,
    };
  },
  mounted() {
    this.subscriptionScroll();
    this.tierScroll();
  },
  methods: {
    subscriptionScroll() {
      const tl = gsap.timeline({
        scrollTrigger: {
          start: "top 70%",
          end: "top 50%",
          trigger: ".price",
          scrub: 5,
        },
      });
      tl.to(".detail.one", {
        opacity: 1,
        y: 0,
        duration: 2,
      })
        .to(
          ".detail.two",
          {
            opacity: 1,
            y: 0,
            duration: 2,
          },
          "<50%"
        )
        .to(
          ".detail.three",
          {
            opacity: 1,
            y: 0,
            duration: 2,
          },
          "<50%"
        );
    },
    tierScroll() {
      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: ".tiers",
          start: "top 80%",
          end: "top 50%",
          scrub: 5,
        },
      });
      tl.from(".tier.one", {
        opacity: 0,
        x: -100,
      }).from(
        ".tier.two",
        {
          opacity: 0,
          x: 100,
        },
        "<"
      );
    },
  },
};
</script>

<style></style>
