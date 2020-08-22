<template>
  <div class="container">
    <header class="text-center">
      <h1 class="text-6xl mt-2">
        Javascript Snippets
      </h1>
      <h2 class="text-2xl my-8">
        A free to use, open source, collection of <br />Javascript Snippets
      </h2>
    </header>

    <main>
      <section class="text-center">
        <label for="search">Search all snippets:</label>
        <br />
        <input
          type="text"
          id="search"
          v-model="search"
          class="border rounded p-4 w-1/2 my-4"
        />
        <p>Or, filter by keyword:</p>
        <ul>
          <li @click="search = 'array'">array</li>
          <li @click="search = 'object'">object</li>
          <li @click="search = 'number'">number</li>
          <li @click="search = 'string'">string</li>
        </ul>
      </section>

      <section class="mt-8">
        <h3 class="text-2xl" v-if="!search">Recently added:</h3>
        <div v-for="snippet in filteredList" :key="snippet.slug">
          <snippet :snippet="snippet"></snippet>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import Snippet from '../components/Snippet'
export default {
  components: { Snippet },
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' },
        { src: '/prism.js', defer: true },
      ],
    }
  },
  data: function () {
    return {
      search: '',
    }
  },
  computed: {
    filteredList() {
      if (!this.search) return this.snippets
      return this.snippets.filter((snippet) =>
        // to string first to allow partial matches
        // i.e. "mi" will return "min" term when typing, includes alone will wait for a full match
        snippet.tags.toString().includes(this.search.toLowerCase())
      )
    },
  },
  async asyncData({ $content }) {
    const snippets = await $content('snippets').fetch()

    return {
      snippets,
    }
  },
}
</script>

<style></style>
