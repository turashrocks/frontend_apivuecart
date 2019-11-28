<template>
 <div>
     <v-expansion-panels>

      <template v-for="category in categories">
        <template v-if="category.children.length">
          <v-expansion-panel :key="category.slug">
            <nuxt-link
                :to="{ name: 'categories-slug', params: { slug: category.slug } }"
              >
            <v-expansion-panel-header>
                {{ category.name }}
                
                </v-expansion-panel-header>
            </nuxt-link>
            <nuxt-link
                        :to="{ name: 'categories-slug', params: { slug: child.slug } }"
                        v-for="child in category.children"
                        :key="child.slug"
                        >
                    <v-expansion-panel-content>
                    <!-- <h3>Lorem</h3> -->
                    
                        <h3>{{ child.name }}</h3>
                        
                    </v-expansion-panel-content>
            </nuxt-link>
          </v-expansion-panel>
        </template>
        <template v-else>
            <!-- <nuxt-link :to="{ name: 'categories-slug', params: { slug: category.slug } }" :key="category.slug" class="navbar-item">
              {{ category.name }}
            </nuxt-link> -->
             <v-expansion-panel :key="category.slug">
                <v-expansion-panel-header>
                    <nuxt-link
                    :to="{ name: 'categories-slug', params: { slug: category.slug } }"
                    >{{ category.name }}
                    </nuxt-link>
                </v-expansion-panel-header>
                <v-expansion-panel-content>
                <!-- <h3>Lorem</h3> -->
                </v-expansion-panel-content>
          </v-expansion-panel>
          </template>
      </template>
        <!-- <v-expansion-panel>
          <v-expansion-panel-header>Item 2</v-expansion-panel-header>
          <v-expansion-panel-content>
             <h3>Lorem</h3>
          </v-expansion-panel-content>
        </v-expansion-panel>

        <v-expansion-panel>
          <v-expansion-panel-header>Item 3</v-expansion-panel-header>
          <v-expansion-panel-content>
            <h3>Lorem</h3>
          </v-expansion-panel-content>
        </v-expansion-panel>

        <v-expansion-panel>
          <v-expansion-panel-header>Item 4</v-expansion-panel-header>
          <v-expansion-panel-content>
            <h3>Lorem</h3>
          </v-expansion-panel-content>
        </v-expansion-panel> -->

    </v-expansion-panels> 
 </div>
</template>

<script>
  import { mapGetters } from 'vuex'

  export default {
    computed: {
      ...mapGetters({
        categories: 'categories'
        // cartCount: 'cart/count'
      })
    }
  }
</script>