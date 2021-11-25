<template>
  <article>
    <nuxt-content :document="info" />
  </article>
</template>

<script>
  export default {
    async asyncData({ $content, params }) {
      const info = await $content('profile', params.slug).fetch()
      return { info }
    }
  }
</script>