<template>
<v-main>
  <v-container>
    <Header  :siteInfo="siteInfo" :pageInfo="pageInfo" />
    <section>
      <div class="text-center mt-8">
        <h2 class="text-3xl font-bold">Profile List</h2>
      </div>
      <ul>
        <li v-for="(post, index) in posts" :key="index">
          <div class="mb-4">
            <h3 class="text-xl font-bold mb-2"><NuxtLink :to="`/profile/${post.slug}`">{{index+1}}.  {{ post.title }}</NuxtLink></h3>
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
        name: 'profile',
      }
    }
  },
  async asyncData ({ $content }) {
    const siteInfo = await $content('site-info').fetch()
    const posts = await $content("profile")
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
