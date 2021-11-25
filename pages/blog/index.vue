<template>
<v-main>
  <v-container>
    <Header  :siteInfo="siteInfo" :pageInfo="pageInfo" />
    <section>
      <div class="text-center mt-8">
        <h2 class="text-3xl font-bold">Blog Posts</h2>
      </div>
      <ul>
        <li v-for="(post, index) in posts" :key="index">
          <div class="mb-4">
            <h3 class="text-xl font-bold mb-2"><NuxtLink :to="`/blog/${post.slug}`">{{index+1}}.  {{ post.title }}</NuxtLink></h3>
            <h4>- Date: {{post.date}}</h4>
            <h4>- Keywords: {{post.description}}</h4>
            <nuxt-content
              class="bg-gray-200 mt-2 mb-8 mx-4"
              :document="post"
            />
          </div>
        </li>
      </ul>
    </section>
    <Footer :info="siteInfo" />
  </v-container>
</v-main>
</template>
<script>
export default {

  data() {
    return {
      // Custom page data comes here.
      pageInfo: {
        name: 'blog',
      }
    }
  },
  async asyncData ({ $content }) {
    const siteInfo = await $content('site-info').fetch()
    const posts = await $content("blog")
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
    onLoad() {
      alert('test');
    }
  }
}
</script>
