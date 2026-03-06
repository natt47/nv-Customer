<template>
  <div>
    <h1>Show Book</h1>

    <p>Book ID: {{ book.id }}</p>
    <p>Title: {{ book.title }}</p>
    <p>Author: {{ book.author }}</p>

    <router-link :to="{ name: 'books' }">
      <button>กลับ</button>
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      book: {}
    }
  },

  created() {
    const bookId = this.$route.params.bookId

    const books = [
      { id: 1, title: "Vue.js Guide", author: "Evan You" },
      { id: 2, title: "Node.js Basics", author: "Ryan Dahl" }
    ]

    this.book = books.find(book => book.id == bookId)
  }
}
</script>

<style scoped>
</style>