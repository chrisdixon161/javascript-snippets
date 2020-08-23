<template>
  <article class="snippet">
    <!-- display tags in each snippet -->
    <!-- add author to snippet -->
    <h3 class="text-2xl" @click="selected = !selected">{{ snippet.title }}</h3>
    <popup :snippet="snippet" v-show="selected"></popup>
  </article>
</template>

<script>
export default {
  props: ['snippet'],
  data() {
    return {
      selected: false,
    }
  },
}
</script>

<style scoped>
article {
  margin: 40px 0;
  padding: 20px;
  border: 1px solid gray;
}

article:hover {
  /* background: rgb(246, 246, 246); */
  cursor: pointer;
}
</style>
