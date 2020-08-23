<template>
  <article>
    <div v-html="$md.render(snippet.body)" />
  </article>
</template>
<script>
export default {
  props: ['snippet'],
}
</script>
<style scoped></style>
