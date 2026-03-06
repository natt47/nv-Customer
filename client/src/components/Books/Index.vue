<template>
  <div>
    <h1>Books</h1>

    <p>จำนวน Book {{ books.length }}</p>

    <router-link :to="{ name: 'books-create' }">
      <button>สร้าง Book</button>
    </router-link>

    <br><br>

    <table border="1" cellpadding="10">
      <thead>
        <tr>
          <th>ID</th>
          <th>Title</th>
          <th>Author</th>
          <th>Action</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="book in books" :key="book.id">
          <td>{{ book.id }}</td>
          <td>{{ book.title }}</td>
          <td>{{ book.author }}</td>

          <td>
            <router-link :to="{ name: 'book', params: { bookId: book.id }}">
              ดู
            </router-link>

            |

            <router-link :to="{ name: 'book-edit', params: { bookId: book.id }}">
              แก้ไข
            </router-link>

            |

            <button @click="deleteBook(book.id)">ลบ</button>
          </td>
        </tr>
      </tbody>
    </table>

  </div>
</template>

<script>
export default {
  data() {
    return {
      books: [
        { id: 1, title: "Vue.js Guide", author: "Evan You" },
        { id: 2, title: "Node.js Basics", author: "Ryan Dahl" }
      ]
    }
  },

  methods: {
    deleteBook(id) {
      if (confirm("ต้องการลบข้อมูลหรือไม่")) {
        this.books = this.books.filter(book => book.id !== id)
      }
    }
  }
}
</script>