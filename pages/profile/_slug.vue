<template>
<v-main>
  <v-container>
    <Header  :siteInfo="siteInfo" :pageInfo="pageInfo" />
    <section>
      <div class="text-center mt-8">
        <h2 class="text-3xl font-bold">[{{post.name}}] Profile</h2>
      </div>
      <div class="mb-4">
        <h3 v-text="post.title" class="text-xl font-bold mb-2"></h3>
        <div class="text-center my-4 mx-auto">
          <nuxt-img :src="post.picture" 
                    :alt="post.name" 
                    sizes="sm:100vw md:50vw lg:600px" />
        </div>
        <h4>- Name: {{post.name}}</h4>
        <h4>- Date of Birth: {{post.dateofbirth}}</h4>
        <h4>- Details</h4>
        <nuxt-content
          class="bg-gray-200 mt-2 mb-8 mx-4"
          :document="post"
        />
      </div>
    </section>
    <Footer :info="siteInfo" />
  </v-container>
</v-main>
</template>
<style scoped>
.container {
  padding-top: 0px !important;
}
</style>
<script>
export default {
  data() {
    return {
      // Custom page data comes here.
      pageInfo: {
        name: 'profile',
      }
    }
  },
  async asyncData({ $content, params }) {
    const siteInfo = await $content('site-info').fetch()
    const post = await $content('profile', params.slug).fetch()
    return { siteInfo, post }
  }
}
</script>
