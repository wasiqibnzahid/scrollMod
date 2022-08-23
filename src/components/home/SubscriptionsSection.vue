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
        <div class="detail">
          <div class="price-detail"><span>$</span>5</div>
          <div class="description">
            for each Auto-Tune Unlimited Monthly Subscription Trial
          </div>
        </div>
        <div class="detail">
          <div class="price-detail"><span>$</span>30</div>
          <div class="description">
            for each paid Auto-Tune Unlimited Monthly Subscription sold for
            $24.99
          </div>
        </div>
        <div class="detail">
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
        <div class="tier">
          <div class="head">Tier 1</div>
          <p>
            For each sale of any perpetual plug-in license, affiliates are paid
            10% of the price listed on our website. This includes licenses for
            every edition of Auto-Tune and every vocal effect sold on our
            website.
          </p>
          <p class="tier-note">(Note that it does not include upgrades.)</p>
        </div>
        <div class="tier">
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
export default {
  data() {
    return {
      itemTop: 0,
      tierTop: 0,
    };
  },
  mounted() {
    // Price Section Observer
    const priceObserver = new IntersectionObserver((change) => {
      if (change[0].isIntersecting) {
        if (this.itemTop == 0) {
          this.itemTop = window.scrollY;
        }
        window.addEventListener("scroll", this.subscriptionScroll);
      } else {
        window.removeEventListener("scroll", this.subscriptionScroll);
      }
    });
    priceObserver.observe(this.$refs.priceContainer);

    const tierObserver = new IntersectionObserver((change) => {
      if (change[0].isIntersecting) {
        if (this.tierTop == 0) {
          this.tierTop = window.scrollY;
        }
        window.addEventListener("scroll", this.tierScroll);
      }
    });
    tierObserver.observe(this.$refs.tierContainer);
  },
  methods: {
    subscriptionScroll() {
      const scroll = window.scrollY;
      this.priceItems.forEach((x, i) => {
        if (scroll > this.itemTop - 50 && scroll < this.itemTop + 150) {
          x.style.opacity = "0";
          x.style.transform = "translateY(30%)";
        } else if (scroll > this.itemTop + 150 && scroll < this.itemTop + 200) {
          if (i == 0) {
            x.style.opacity = "0.5";
            x.style.transform = "translateY(20%)";
          } else {
            x.style.opacity = "0";
            x.style.transform = "translateY(30%)";
          }
        } else if (scroll > this.itemTop + 200 && scroll < this.itemTop + 250) {
          if (i == 0) {
            x.style.opacity = "1";
            x.style.transform = "translateY(0)";
          } else if (i == 1) {
            x.style.opacity = "0.5";
            x.style.transform = "translateY(20%)";
          } else {
            x.style.opacity = "0";
            x.style.transform = "30%";
          }
        } else if (scroll > this.itemTop + 250 && scroll < this.itemTop + 300) {
          if (i != 2) {
            x.style.opacity = "1";
            x.style.transform = "translateY(0)";
          } else {
            x.style.opacity = "0.5";
            x.style.transform = "translateY(20%)";
          }
        } else if (scroll > this.itemTop + 300) {
          x.style.opacity = "1";
          x.style.transform = "translateY(0)";
        }
      });
    },
    tierScroll() {
      const scroll = window.scrollY;
      this.tierItems.forEach((x, i) => {
        if (scroll > this.tierTop && scroll < this.tierTop + 50) {
          x.style.opacity = "0";
          if (i == 0) {
            x.style.transform = "translateX(-50%)";
          } else {
            x.style.transform = "translateX(50%)";
          }
        } else if (scroll > this.tierTop + 50 && scroll < this.tierTop + 100) {
          x.style.opacity = "0.2";
          if (i == 0) {
            x.style.transform = "translateX(-20%)";
          } else {
            x.style.transform = "translateX(20%)";
          }
        } else if (scroll > this.tierTop + 150 && scroll < this.tierTop + 200) {
          x.style.opacity = "0.4";
          if (i == 0) {
            x.style.transform = "translateX(-15%)";
          } else {
            x.style.transform = "translateX(15%)";
          }
        } else if (scroll > this.tierTop + 200 && scroll < this.tierTop + 250) {
          x.style.opacity = '0.7'
          if (i == 0) {
            x.style.transform = "translateX(-10%)";
          } else {
            x.style.transform = "translateX(10%)";
          }
        }
        else if (scroll > this.tierTop + 250 && scroll < this.tierTop + 300) {
x.style.opacity = '0.85'
if(i == 0) {
  x.style.transform = 'translateX(-5%)'
}
else {
  x.style.transform = 'translateX(5%)'

}

        }
        else if (scroll > this.tierTop + 300) {
          x.style.transform = 'translateX(0)'
          x.style.opacity = '1'
        }
      });
    },
  },
  computed: {
    priceItems() {
      return this.$refs.priceContainer.querySelectorAll(".detail");
    },
    tierItems() {
      return this.$refs.tierContainer.querySelectorAll(".tier");
    },
  },
};
</script>

<style></style>
