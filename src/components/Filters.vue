<template>
  <h1>Filters</h1>

  <label for="search">
    Search
    <input
      id="search"
      v-model="term"
      @keypress.enter="search(term)"
    />
  </label>

  <p
    v-for="filter in filters"
    :key="filter"
    @click="() => filterPosts(filter)"
  >
    {{ filter }}
  </p>
</template>

<script>
const filters = [
  'All',
  'HVAC',
  'Overhead Doors'
]

export default {
  props: [
    'filterPosts',
    'search',
    'filteredPosts'
  ],
  data () {
    return {
      filters,
      term: ''
    }
  }
}
</script>
