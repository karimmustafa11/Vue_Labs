<template>
    <div>
      <h3>Book List</h3>
      <ul class="list-group mb-4">
        <li v-for="book in books" :key="book.ISBN"
            class="list-group-item d-flex justify-content-between align-items-center">
          <span>{{ book.Name }}</span>
          <span class="badge bg-primary">{{ book.author }}</span>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BookList',
    props: {
      books: {
        type: Array,
        required: true
      }
    }
  }
  </script>