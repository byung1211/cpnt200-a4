<template>
  <article>
    <nuxt-content :document="code" />
  </article>
</template>

<script>
  export default {
    async asyncData({ $content, params }) {
      const code = await $content('code-snippet', params.slug).fetch()
      return { code }
    }
  }
</script>