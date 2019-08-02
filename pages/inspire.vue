<template>
  <section class="section">
    <h2 class="title is-3 has-text-grey">
      "Just start  <b-icon
        icon="rocket"
        size="is-large"
      />"
    </h2>
    <h3 class="subtitle is-6 has-text-grey">
      Author: <a href="https://github.com/anteriovieira">
        Antério Vieira
      </a>
    </h3>
    <button @click="checkoutRedirect">Checkout With redirect</button>
  </section>
</template>

<script>
export default {
  methods: {
    checkoutRedirect() {
      console.log(this.$stripe)
      this.$stripe.redirectToCheckout({
        items: [
          // Replace with the ID of your SKU
          {sku: 'sku_FY5ZRSsPPnNbAF', quantity: 1}
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
