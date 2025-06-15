<template>
    <div class="row g-4 mb-4">
      <div class="col-md-4" v-for="book in books" :key="book.ISBN">
        <div class="card h-100" :class="book.numberofpage < 50 ? 'less' : 'more'">
          <img :src="book.image" class="card-img-top book-img" :alt="book.Name">
          <div class="card-body">
            <h5 class="card-title">{{ book.Name }}</h5>
            <div class="row mb-2">
              <div class="col-6"><span class="badge bg-info w-100">{{ book.category }}</span></div>
              <div class="col-6"><span class="badge bg-secondary w-100">{{ book.author }}</span></div>
            </div>
            <div class="row mb-2">
              <div class="col-6"><span class="badge bg-warning text-dark w-100">#{{ book.numberofpage }} Pages</span></div>
              <div class="col-6"><span class="badge bg-success w-100">{{ formatPrice(book.price) }}</span></div>
            </div>
            <div class="row mb-2">
              <div class="col-6"><span class="badge bg-dark w-100">ISBN: {{ book.ISBN }}</span></div>
              <div class="col-6"><button class="btn btn-primary w-100" @click="$emit('add-to-wishlist', book)">Add To List</button></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BookCards',
    props: {
      books: {
        type: Array,
        required: true
      }
    },
    methods: {
      formatPrice(price) {
        return new Intl.NumberFormat('ar-SA', { style: 'currency', currency: 'EGP' }).format(price);
      }
    }
  }
  </script>