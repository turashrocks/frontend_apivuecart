<template>
      <div class="columns">
        <div class="column is-half">
          <!-- <img src="http://via.placeholder.com/620x620" alt="Product name"> -->
          <div class="card" style="background-color: transparent; box-shadow: none;">
            <div class="card-content">
              <div class="card-carousel">
                <div class="card-img">
                  <img :src="currentImage" alt="">
                    <div class="actions">
                      <span @click="prevImage" class="prev">
                        <i class="fas fa-chevron-left"></i>
                      </span>
                      <span @click="nextImage" class="next">
                        <i class="fas fa-chevron-right"></i>
                      </span>
                    </div>
                  </div>
                <div class="thumbnails">
                  <div
                    v-for="(image, index) in  images"
                    :key="image.id"
                    :class="['thumbnail-image', (activeImage == index) ? 'active' : '']"
                    @click="activateImage(index)"
                  >
                    <img :src="image.thumb">
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="column is-half">
            <h1 class="title is-4">
              {{ product.name }}
            </h1>
            <p v-if="product.description">
              {{ product.description }}
            </p>

            <hr>

            <!-- <span class="tag is-rounded is-medium is-dark" v-if="!product.in_stock"> -->
            <span class="tag is-rounded is-medium is-dark">
              Out of stock
            </span>

            <span class="tag is-rounded is-medium">
              {{ product.price }}
            </span>

            <!-- START for Radios -->
              <v-data-table
                :headers="headers"
                :items="desserts"
                :single-select="singleSelect"
                item-key="name"
                show-select
                class="elevation-1"
                hide-default-footer
              >

              </v-data-table>
            <!-- END for Radios -->
            <v-container class="grey lighten-5">
              <v-row no-gutters>
                <v-col
                  cols="12"
                  sm="4"
                >
                  <IncrementDecrement :value="50" :min="5" :max="55"></IncrementDecrement>
                </v-col>

                <v-col
                  cols="12"
                  sm="4"
                >
                </v-col>
                <v-col
                  cols="12"
                  sm="4"
                >
                  <div class="control" style="float: right;">
                    <button type="submit" class="button is-info">Add to cart</button>
                  </div>
                </v-col>
              </v-row>
            </v-container>



        </div>
      </div>
</template>

<script>
import IncrementDecrement from '@/components/products/IncrementDecrement'

export default{
  data () {
      return {
        product: null,
        // form: {
        //   variation: '',
        //   quantity: 1
        // }
  // START for Radios
        singleSelect: true,
        selected: [],
        headers: [
          {
            text: 'Quantity',
            align: 'left',
            value: 'name',
          },
          { text: 'Unit', value: 'unit' },
          { text: 'Discount', value: 'calories' },
          { text: 'Price', value: 'carbs' },
        ],
        desserts: [
          {
            name: '10 - 49',
            unit: 'kg',
            calories: 159,
            carbs: 24,
          },
          {
            name: '50 - 99',
            unit: 'kg',
            calories: 237,
            carbs: 37,
          },
          {
            name: '100 - 150',
            unit: 'kg',
            calories: 262,
            carbs: 23,
          }
        ],
  // END for Radios
  // START for Carousal
        images: [
          {
            id: '1',
            big: '/images/p1.jpeg',
            thumb: '/images/thumbs/p1.jpeg'
          },
          {
            id: '2',
            big: '/images/p2.jpeg',
            thumb: '/images/thumbs/p2.jpeg'
          },
          {
            id: '3',
            big: '/images/p3.jpeg',
            thumb: '/images/thumbs/p3.jpeg'
          },
          {
            id: '4',
            big: '/images/p4.jpeg',
            thumb: '/images/thumbs/p4.jpeg'
          }
        ],
        activeImage: 0
      }
  },
  components: {
      IncrementDecrement
  },
  computed: {
    currentImage() {
      return this.images[this.activeImage].big;
    }
  },
  methods: {
    nextImage() {
      var active = this.activeImage + 1;
      if(active >= this.images.length) {
        active = 0;
      }
      this.activateImage(active);
    },
    prevImage() {
      var active = this.activeImage - 1;
      if(active < 0) {
        active = this.images.length - 1;
      }
      this.activateImage(active);
    },
    activateImage(imageIndex) {
      this.activeImage = imageIndex;
    }
  },
  // END for Carousal
  async asyncData ({ params, app }) {
      let response = await app.$axios.$get(`products/${params.slug}`)

      return {
        product: response.data
      }
  }
}

</script>
<!--<script>
  import { mapActions } from 'vuex'

  import ProductVariation from '@/components/products/ProductVariation'

  export default {
    data () {
      return {
        product: null,
        form: {
          variation: '',
          quantity: 1
        }
      }
    },

    watch: {
      'form.variation' () {
        this.form.quantity = 1
      }
    },

    components: {
      ProductVariation
    },

    methods: {
      ...mapActions({
        store: 'cart/store'
      }),

      add () {
        this.store([{
          id: this.form.variation.id, quantity: this.form.quantity
        }])

        this.form = {
          variation: '',
          quantity: 1
        }
      }
    },

    async asyncData ({ params, app }) {
      let response = await app.$axios.$get(`products/${params.slug}`)

      return {
        product: response.data
      }
    }
  }
</script>-->
