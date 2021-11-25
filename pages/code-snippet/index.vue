<template>
<v-main>
  <v-container>
    <Header  :siteInfo="siteInfo" :pageInfo="pageInfo" />
    <section>
      <div class="text-center mt-8">
        <h2 class="text-3xl font-bold">Code Snippet List</h2>
      </div>
      <ul>
        <li v-for="(post, index) in posts" :key="index">
          <div class="mb-4">
            <h3 class="text-xl font-bold mb-2"><NuxtLink :to="`/code-snippet/${post.slug}`">{{index+1}}.  {{ post.title }}</NuxtLink></h3>
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
        </li>
      </ul>
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
  async asyncData ({ $content }) {
    const siteInfo = await $content('site-info').fetch()
    const posts = await $content("code-snippet")
      .sortBy("createdAt", "desc")
      // .only(["title", "path"])
      .fetch()
      .catch((err) => {
        error({ statusCode: 404, message: "Page not found" });
      });

    console.log(posts)
    
    return {
      siteInfo, posts
    }
  },
  methods: {
  }
}
</script>
