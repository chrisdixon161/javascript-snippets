<template>
  <article class="snippet">
    {{ snippet.title }}
    <div v-html="$md.render(snippet.body)" />
  </article>
</template>

<script>
export default {
  props: ['snippet'],
}
</script>

<style scoped>
.snippet-post {
  margin: 40px 0;
  padding: 20px;
}

.snippet:hover {
  background: rgb(246, 246, 246);
}
</style>
