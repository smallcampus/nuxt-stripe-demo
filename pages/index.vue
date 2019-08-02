<template>
  <section class="section">
    <div class="columns is-mobile">
      <card title="Stripe" icon="cellphone-link">
        <b-input placeholder="sku" v-model="sku"></b-input>
        <div class="button" @click="checkoutRedirect">Checkout With Stripe redirect</div>
      </card>
      <card
        title="Free"
        icon="github-circle"
      >
        Open source on <a href="https://github.com/buefy/buefy">
          GitHub
        </a>
      </card>

      <card
        title="Responsive"
        icon="cellphone-link"
      >
        <b class="has-text-grey">
          Every
        </b> component is responsive
      </card>

      <card
        title="Modern"
        icon="alert-decagram"
      >
        Built with <a href="https://vuejs.org/">
          Vue.js
        </a> and <a href="http://bulma.io/">
          Bulma
        </a>
      </card>

      <card
        title="Lightweight"
        icon="arrange-bring-to-front"
      >
        No other internal dependency
      </card>
    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'

export default {
  name: 'HomePage',
  data() {
    return {
      sku: 'sku_FY5ZRSsPPnNbAF'
    }
  },
  components: {
    Card
  },
  methods: {
    checkoutRedirect() {
      console.log(this.$stripe)
      this.$stripe.redirectToCheckout({
        items: [
          // Replace with the ID of your SKU
          {sku: this.sku, quantity: 1}
        ],
        successUrl: 'https://example.com/success',
        cancelUrl: 'https://example.com/cancel',
      }).then((result) => {
        // If `redirectToCheckout` fails due to a browser or network
        // error, display the localized error message to your customer
        // using `result.error.message`.
      });
    }
  }
}
</script>
