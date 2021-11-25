<template>
  <footer class="border-t border-gray-200 my-2">
    <div class="container flex flex-wrap items-center justify-center py-2 mx-auto">
      <h4 v-html="'&copy;' + info.copyright"></h4>
    </div>
  </footer>
</template>
<script>
export default {
  props: ['info']
}
</script>
