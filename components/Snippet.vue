<template>
  <article class="snippet">
    <!-- display tags in each snippet -->
    <h3 class="text-2xl">{{ snippet.title }}</h3>
    <div v-html="$md.render(snippet.body)" />
  </article>
</template>

<script>
export default {
  props: ['snippet'],
}
</script>

<style scoped>
article {
  margin: 40px 0;
  padding: 20px;
  border: 1px solid gray;
}

article:hover {
  background: rgb(246, 246, 246);
}
</style>
