<template>
  <div class="section application">
    <h2>Auto-Tune Affiliate Application</h2>
    <form class="Registration">
      <div class="form" ref="form">
        <div class="inputContainer" v-if="activeItem == 0">
          Name:
          <input placeholder="First name..." />
          <input placeholder="Last name..." />
        </div>
        <div v-else-if="activeItem == 1">
          Contact Info:
          <input placeholder="Email" />
          <input placeholder="City" />
          <select placeholder="Country...">
            <option value="" selected>Country...</option>
            <option value="usa">USA</option>
            <option value="canada">Canada</option>
            <option value="uk">United Kingdom</option>
          </select>
        </div>
        <div v-else-if="activeItem == 2">
          Social Media:
          <div class="flex align-center">
            +
            <select style="margin-left: 10px; width: 30%">
              <option value="facebook" selected>Facebook</option>
              <option value="instagram">Instagram</option>
              <option value="website">Website</option>
              <option value="other">Other</option>
            </select>
            <input style="width: 65%" placeholder="Last name..." />
          </div>
        </div>
        <div v-else-if="activeItem == 3">
          What is your approximate reach?
          <select>
            <option value="0" selected>Select...</option>
            <option value="a">0 - 10,000</option>
            <option value="b">10,000 - 100,000</option>
            <option value="c">100,000 - 500.000</option>
            <option value="d">500,000 - 1,000,000</option>
          </select>
        </div>
        <div v-else-if="activeItem == 4">
          What describes you best?
          <select>
            <option value="0" Selected>Select...</option>
            <option value="a">Artist Influencer</option>
            <option value="b">Educational Influencer</option>
            <option value="c">Educational Website / Blog</option>
            <option value="d">Other</option>
          </select>
        </div>
        <div v-else-if="activeItem == 5">
          How many other affiliate programs are you involved with?
          <select>
            <option value="0" selected>Select...</option>
            <option value="a">1 - 3</option>
            <option value="b">3 - 5</option>
            <option value="c">Over 5</option>
          </select>
        </div>
        <div v-else-if="activeItem == 6">
          What is the most successful program for you?
          <select>
            <option value="a" selected>1 - 3</option>
            <option value="b">3 - 5</option>
            <option value="c">Over 5</option>
          </select>
        </div>
        <div v-else-if="activeItem == 7">
          Do any of your other programs sell subscriptions?
          <select>
            <option value="a" selected>Select...</option>
            <option value="b">Yes</option>
            <option value="c">No</option>
          </select>
        </div>
        <div v-else-if="activeItem == 8">
          Do you have any preference in selling subscriptions vs. perpetual
          software products?
          <select>
            <option value="a" selected>Select...</option>
            <option value="b">Subscription</option>
            <option value="c">Perpetual</option>
            <option value="d">No preference</option>
          </select>
        </div>
        <div v-else-if="activeItem == 9">
          Do you have a community you regularly interact with via email list,
          forum, or community site like Discord and Patreon?
          <select>
            <option value="a" selected>Select...</option>
            <option value="b">Yes</option>
            <option value="c">No</option>
          </select>
        </div>
        <div v-else-if="activeItem == 10">
          If you have a community, how big is it?
          <select>
            <option value="a" selected>Select...</option>
            <option value="b">n/a</option>
            <option value="c">0 - 10,000</option>
            <option value="d">10,000 - 100,000</option>
            <option value="e">100,000 - 500,000</option>
            <option value="f">500,000 - 1,000,000</option>
            <option value="g">over 1,000,000</option>
          </select>
        </div>
        <div v-else-if="activeItem == 11">
          What types of promotions work best for you?
          <select>
            <option value="a" selected>Select...</option>
            <option value="b">n/a</option>
            <option value="c">0 - 10,000</option>
            <option value="d">10,000 - 100,000</option>
            <option value="e">100,000 - 500,000</option>
            <option value="f">500,000 - 1,000,000</option>
            <option value="g">over 1,000,000</option>
          </select>
        </div>
        <div v-else-if="activeItem == 12">
          On a scale of 1-5 (with 5 being most important) how important is
          income from affiliate sales to you??
          <select>
            <option value="a" selected>Select...</option>
            <option v-for="item in 5" :key="item" :value="item">
              {{ item }}
            </option>
          </select>
        </div>
        <div class="button">
          <button type="button" v-show="activeItem > 0" @click="previousItem">
            Previous
          </button>
          <button type="button" @click="nextItem">
            {{ activeItem == 12 ? "Submit" : "Next" }}
          </button>
        </div>
        <div class="activeButtons">
          <div
            v-for="item in 13"
            :key="item"
            class="circle"
            :class="
              activeItem == item - 1
                ? 'active'
                : activeItem > item - 1
                ? 'completed'
                : ''
            "
          ></div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeItem: 0,
    };
  },
  methods: {
    previousItem() {
      if (this.activeItem > 0) {
        this.activeItem = this.activeItem - 1;
      }
    },
    nextItem() {
      const inputArr = this.$refs.form.querySelectorAll("input, select");
      var isEmpty = false;
      inputArr.forEach((x) => {
        if (x.value == "") {
          isEmpty = true;
        }
      });
      if (this.activeItem < 12 && !isEmpty) {
        this.activeItem = this.activeItem + 1;
      } else if (this.activeItem == 12) {
        this.$router.go();
      } else if (isEmpty) {
        inputArr.forEach((x) => {
          if (x.value == "") {
            x.style.background = "red";
            setTimeout(() => {
              x.style.background = "";
            }, 3000);
          }
        });
      }
    },
  },
};
</script>

<style></style>
