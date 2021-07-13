<template>
  <div class="container">
    <div class="half">
      <Filters
        :filterPosts="filterPosts"
        :search="search"
        :filteredPosts="filteredPosts"
      />
    </div>
    <div class="half">
      <Posts :posts="posts" />
    </div>
  </div>
</template>

<script>
import Filters from './components/Filters.vue'
import Posts from './components/Posts.vue'

import MOCK_DATA from './MOCK_DATA.json'

export default {
  name: 'App',
  components: {
    Filters,
    Posts
  },
  data () {
    return {
      posts: MOCK_DATA,
      str: '',
      type: ''
    }
  },
  // computed: {
  //   filteredPosts: {
  //     get () {
  //       return this.posts
  //     },
  //     set () {
  //       this.posts = MOCK_DATA
  //       const results = this.posts.filter((post) => {
  //         if (this.type === "filter") {
  //           return post.category === this.str
  //         } else {
  //           return post.title.toLowerCase().includes(this.str.toLowerCase())
  //         }
  //       })
  //       this.posts = results
  //     }
  //   }
  // },
  methods: {
    filterPosts (catName) {
      this.resetPosts()
      if (catName !== 'All') {
        this.posts = this.posts.filter((post) => {
          return post.category === catName
        })
      }
    },
    search (term) {
      this.resetPosts()
      this.posts = this.posts.filter((post) => {
        return post.title.toLowerCase().includes(term.toLowerCase())
      })
    },
    resetPosts () {
      this.posts = MOCK_DATA
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  margin: 20px;
}
.half {
  width: 40%;
}
</style>
