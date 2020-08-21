<template>
  <article class="snippet">
    {{ snippet.title }}
    <div v-html="$md.render(snippet.body)" />
  </article>
</template>

<script>
export default {
  props: ['snippet'],
  head() {
    return {
      script: [{ src: '/prism.js', defer: true }],
    }
  },
}
</script>

<style scoped>
.snippet-post {
  margin: 40px 0;
  padding: 20px;
  border: 1px solid lightblue;
}

.snippet:hover {
  background: rgb(246, 246, 246);
}
</style>
