<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        javascript-snippets
      </h1>

      <section class>
        <label for="search">Search all posts:</label>
        <input type="text" id="search" v-model="search" />
      </section>

      <section>
        <h3 v-if="!search">Recently added:</h3>
        <div v-for="snippet in filteredList" :key="snippet.slug">
          <snippet :snippet="snippet"></snippet>
        </div>
      </section>
    </div>
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

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
