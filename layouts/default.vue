<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="$vuetify.breakpoint.lgAndUp"
      app
      src="https://cdn.vuetifyjs.com/images/backgrounds/bg-2.jpg"
    >
      <LeftSidebar/>
    </v-navigation-drawer>

    <v-app-bar
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      app
      color="blue darken-3"
      dark
      src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
    >
      <v-toolbar-title
        style="width: 300px"
        class="ml-0"
      >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
          <span class="white-header hidden-sm-and-down">
            <nuxt-link
              :to="{ name: 'index'}"
              >
              Vitabari Development
            </nuxt-link>
          </span>
      </v-toolbar-title>
      <v-text-field
        flat
        solo-inverted
        hide-details
        prepend-inner-icon="mdi-magnify"
        label="Search"
        class="hidden-sm-and-down"
      />
      <v-spacer />

       <v-toolbar-items>
       <template v-if="!$auth.loggedIn">
            <v-btn text>
              <nuxt-link :to="{ name: 'auth-signin' }">
                Sign In
              </nuxt-link>
            </v-btn>
          </template>
          <template v-else>
            <a href="#">
              {{ $auth.user.name }}
            </a>
            <v-btn text>
              <nuxt-link :to="{ name: 'orders' }">
                Orders
              </nuxt-link>
            </v-btn text>
            <v-btn text>
              <nuxt-link :to="{ name: 'cart' }">
                Cart ({{ cartCount }})
              </nuxt-link>
            </v-btn text>
          </template>


        </v-toolbar-items>

    </v-app-bar>
    <v-content>
      <v-container class="pa-0">
        <nuxt />
      </v-container>
    </v-content>
    <v-btn
      bottom
      color="pink"
      dark
      fab
      fixed
      right
      @click="dialog = !dialog"
    >
      <v-icon>mdi-plus</v-icon>
    </v-btn>
    <v-dialog
      v-model="dialog"
      width="800px"
    >
      <v-card>
        <v-card-title class="grey darken-2">
          Create contact
        </v-card-title>
        <v-container>
          <v-row class="mx-2">
            <v-col
              class="align-center justify-space-between"
              cols="12"
            >
              <v-row
                align="center"
                class="mr-0"
              >
                <v-avatar
                  size="40px"
                  class="mx-3"
                >
                  <img
                    src="//ssl.gstatic.com/s2/oz/images/sge/grey_silhouette.png"
                    alt=""
                  >
                </v-avatar>
                <v-text-field
                  placeholder="Name"
                />
              </v-row>
            </v-col>
            <v-col cols="6">
              <v-text-field
                prepend-icon="business"
                placeholder="Company"
              />
            </v-col>
            <v-col cols="6">
              <v-text-field
                placeholder="Job title"
              />
            </v-col>
            <v-col cols="12">
              <v-text-field
                prepend-icon="mail"
                placeholder="Email"
              />
            </v-col>
            <v-col cols="12">
              <v-text-field
                type="tel"
                prepend-icon="phone"
                placeholder="(000) 000 - 0000"
              />
            </v-col>
            <v-col cols="12">
              <v-text-field
                prepend-icon="notes"
                placeholder="Notes"
              />
            </v-col>
          </v-row>
        </v-container>
        <v-card-actions>
          <v-btn
            text
            color="primary"
          >More</v-btn>
          <v-spacer />
          <v-btn
            text
            color="primary"
            @click="dialog = false"
          >Cancel</v-btn>
          <v-btn
            text
            @click="dialog = false"
          >Save</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-app>
</template>

<script>
import LeftSidebar from '@/layouts/partials/LeftSidebar'
import { mapGetters } from 'vuex'

  export default {
    computed: {
      ...mapGetters({
        categories: 'categories',
        cartCount: 'cart/count'
      })
    },
    components: {
      LeftSidebar
    },
    props: {
      source: String,
    },
    data: () => ({
      dialog: false,
      drawer: null,
      right: false,
      left: false
    }),
  }
</script>
