<template>
  <div class="section">
    <div class="container is-fluid">
      <div class="columns is-centered">
        <div class="column is-three-quarters">
          <h1 class="title is-4">Your cart</h1>

          <article class="message" v-if="products.length">
            <CartOverview />
          </article>
          <p v-else>
            Your cart is empty
          </p>

          <nuxt-link
            :to="{ name: 'checkout' }"
            v-if="!empty"
            class="button is-fullwidth is-info is-medium"
          >
            Checkout
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import { mapGetters } from 'vuex'
  import CartOverview from '@/components/cart/CartOverview'

  export default {
    components: {
      CartOverview
    },

    middleware: [
      //'redirectIfGuest'
    ],

    computed: {
      ...mapGetters({
        empty: 'cart/empty',
        products: 'cart/products'
      })
    }
  }
</script>
