<template>
  <header class="bg-indigo-100 py-3">
    <div class="container flex flex-wrap items-center justify-center py-3 mx-auto">
      <h1 class="text-3xl md:text-4xl font-medium mb-2text-3xl md:text-4xl font-medium mb-2">{{siteInfo.title}}</h1>
    </div>
    <Navigation :pageInfo="pageInfo" />
  </header>
</template>
<script>
export default {
  props: ['siteInfo', 'pageInfo']
}
</script>

