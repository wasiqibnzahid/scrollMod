<template>
  <div class="section FAQ">
    <h2>Faq</h2>
    <div class="FAQ-area" ref="FAQArea">
      <div class="FAQ-data" @click="showOne = !showOne">
        How are purchases tracked?
      </div>
      <div class="FAQ-content" v-show="showOne">
        <p>
          Purchases are tracked via your Impact account and the unique product
          links available there. If your incoming link converts to a sale you
          are paid for the product sale.
        </p>
        <p>
          There is a 30 day cookie which means your customer is allowed a long
          window of time to make their purchasing decision. Note that many
          programs are only 7 days.
        </p>
      </div>
      <div class="FAQ-data" @click="showTwo = !showTwo">
        How can I qualify to be an affiliate?
      </div>
      <div class="FAQ-content" v-show="showTwo">
        <p>Applicants must:</p>
        <ul>
          <li>
            Have an Impact account and <a href="">sign up for our program</a>.
          </li>
          <li>
            Fill out our Applicant form below (Applicants are evaluated on their
            reach, quality of content and any business data of record)
          </li>
        </ul>
      </div>
      <div class="FAQ-data" @click="showThree = !showThree">
        What if I have questions about your program?
      </div>
      <div class="FAQ-content" v-show="showThree">
        <p>
          Please email
          <a href="">marketing@antarestech.com</a>
        </p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      showOne: false,
      showTwo: false,
      showThree: false,
    };
  },
};
</script>

<style></style>
