<template>
  <div class="container">
    <ul class="flex">
      <li class="flex-1 mr-2">
        <NuxtLink to="/" :class="(pageInfo.name === 'home'?navClass.active:navClass.inactive)">
          Home
        </NuxtLink>
      </li>
      <li class="flex-1 mr-2">
        <NuxtLink to="/blog" :class="(pageInfo.name === 'blog'?navClass.active:navClass.inactive)">
          Blog
        </NuxtLink>
      </li>
      <li class="flex-1 mr-2">
        <NuxtLink to="/profile" :class="(pageInfo.name === 'profile'?navClass.active:navClass.inactive)">
          Profile
        </NuxtLink>
      </li>
      <li class="flex-1 mr-2">
        <NuxtLink to="/code-snippet" :class="(pageInfo.name === 'code'?navClass.active:navClass.inactive)">
          Code Snippet
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ['pageInfo'],
  data() {
    return {
      // Custom page data comes here.
      navClass:{
        active: "text-center block border border-blue-500 rounded py-2 px-4 bg-blue-500 text-white",
        inactive:"text-center block border border-white rounded text-blue-500 hover:bg-gray-200 py-2 px-4",
      }
    }
  },
  async asyncData ({ $content }) {
 
    return {
    }
  }
}
</script>
