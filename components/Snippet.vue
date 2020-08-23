<template>
  <article class="snippet" @click="selected = !selected">
    <!-- display tags in each snippet -->
    <!-- add author to snippet -->
    <ul v-for="tag in snippet.tags" :key="tag" class="inline-block space-x-6">
      <li class="border rounded-lg px-4 py-2 mr-4">{{ tag }}</li>
    </ul>
    <h3 class="text-2xl">
      {{ snippet.title }}
    </h3>
    <transition name="fade">
      <popup :snippet="snippet" v-show="selected"></popup>
    </transition>
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

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
