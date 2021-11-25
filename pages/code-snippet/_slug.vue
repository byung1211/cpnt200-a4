<template>
<v-main>
  <v-container>
    <Header  :siteInfo="siteInfo" :pageInfo="pageInfo" />
    <section>
      <div class="text-center mt-8">
        <h2 class="text-3xl font-bold">Code Snippet</h2>
      </div>
      <div class="mb-4">
        <h3 class="text-xl font-bold mb-2">[Title] {{ post.title }}</h3>
        <h4>- Code</h4>
        <div class="bg-gray-200 my-2">
          <pre>
            <code>{{post.code.code}}</code>
          </pre>
        </div>
        <h4>- Description</h4>
        <nuxt-content
          class="bg-gray-200 mb-8"
          :document="post"
        />
      </div>
    </section>
    <Footer  :info="siteInfo" />
  </v-container>
</v-main>
</template>
<script>
export default {
  data() {
    return {
      // Custom page data comes here.
      pageInfo: {
        name: 'code',
      }
    }
  },
  async asyncData({ $content, params }) {
    const siteInfo = await $content('site-info').fetch()
    const post = await $content('code-snippet', params.slug).fetch()
    return { siteInfo, post }
  }
}
</script>
</script>