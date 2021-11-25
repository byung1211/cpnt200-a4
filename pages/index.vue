<template>
  <v-main>
    <v-container>
    
    <Header :siteInfo="siteInfo" :pageInfo="pageInfo"/>

    <section class="flex flex-col mx-10">
      <div class="text-center mt-8 mb-2">
        <h1 class="text-2xl">Hello, I am Alex, How are you doing?</h1>
      </div>
      <div class="text-center my-4 mx-auto">
        <nuxt-img :src="profile.picture" :alt="profile.name" sizes="sm:100vw md:50vw lg:600px" />
      </div>
      <div class="text-center my-2">
        <nuxt-content :document="introInfo" />
      </div>
    </section>
    
    <Footer :info="siteInfo" />
    
    </v-container>
  </v-main>
</template>
<style scoped>

</style>
<script>

import cnavigation from '../components/Navigation.vue'
import cheader from '../components/Header.vue'
import cfooter from '../components/Footer.vue'

export default {

  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
  data() {
    return {
      // Custom page data comes here.
      pageInfo: {
        name: 'home',
      }
    }
  },
  components:{
    cnavigation, cheader, cfooter
  },  
  async asyncData ({ $content }) {
    const introInfo = await $content('intro').fetch()
    const siteInfo = await $content('site-info').fetch()
    const profile = await $content('profile/2021-11-22-this-is-the-first-profile').fetch()
    return {
      introInfo, siteInfo, profile
    }
  }
}
</script>
