<template>
 <div>
   <v-carousel
      :continuous="true"
      hide-delimiter-background
      delimiter-icon="mdi-minus"
      height="400">

    <v-carousel-item>
        <v-row
          align="center"
          justify="center"
        >
          <v-img
              src="/images/ss_pipe1.jpg"
              lazy-src="/images/ss_pipe1.jpg"
              width="auto"
            >
              <div>
              <v-row align="right" justify="end" style="margin-top: 7.5%">
                    <v-col class="text-left" cols="12" sm="4">
                      <div class="my-2 right">
                        <div class="display-3 text-lg-left font-weight-black">
                        <h2>SS Pipe</h2>
                        </div>
                        <v-btn depressed big color="error" :style="{left: '10%', marginTop: '5%'}">Buy Now</v-btn>
                      </div>
                    </v-col>
                </v-row>
            </div>
            </v-img>
        </v-row>
    </v-carousel-item>
    <v-carousel-item>
        <v-row
          align="center"
          justify="center"
        >
          <v-img
              src="/images/ss_pipe2.jpg"
              lazy-src="/images/ss_pipe2.jpg"
              width="auto"
            >
             <div>
              <p class="display-1 text-lg-right text-end font-weight-black" style="margin-right: 80px;">demo_vita</p>
            </div>
            </v-img>
        </v-row>
    </v-carousel-item>
    <v-carousel-item>
        <v-row
          align="center"
          justify="center"
        >
          <v-img
              src="/images/ss_pipe3.jpg"
              lazy-src="/images/ss_pipe3.jpg"
              width="auto"
            >
              <div>
              <p class="display-1 text-lg-right text-end font-weight-black" style="margin-right: 80px;">demo_vita</p>
            </div>
            </v-img>
        </v-row>
    </v-carousel-item>
  </v-carousel>
  <blockquote class="blockquote">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Harum maiores modi quidem veniam, expedita quis laboriosam, ullam facere adipisci, iusto, voluptate sapiente corrupti asperiores rem nemo numquam fuga ab at.</blockquote>
</div>
</template>

<script>

  export default {
    data () {
      return {
        colors: [
          'indigo',
          'warning',
          'pink darken-2',
          'red lighten-1',
          'deep-purple accent-4',
        ],
        slides: [
          'First',
          'Second',
          'Third',
          'Fourth',
          'Fifth',
        ],
        items: [
          {
            src: '/images/ss_pipe1.jpg',
          },
          {
            src: '/images/ss_pipe2.jpg',
          },
          {
            src: '/images/ss_pipe3.jpg',
          }
        ],
      }
    },
  }
</script>
