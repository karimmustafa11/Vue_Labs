<template>
    <div>
      <button class="btn btn-outline-success mb-3" @click="$emit('toggle-wishlist')">Display Wish List</button>
      <div v-if="showWishlist">
        <h3>Wish List</h3>
        <table class="table table-bordered">
          <thead>
            <tr>
              <th>Image</th>
              <th>Name</th>
              <th>Author</th>
              <th>Category</th>
              <th>Pages</th>
              <th>Price</th>
              <th>ISBN</th>
              <th>Remove</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="book in wishlist" :key="book.ISBN">
              <td><img :src="book.image" alt="img" style="height:40px;width:40px;object-fit:cover;"></td>
              <td>{{ book.Name }}</td>
              <td>{{ book.author }}</td>
              <td>{{ book.category }}</td>
              <td>{{ book.numberofpage }}</td>
              <td>{{ formatPrice(book.price) }}</td>
              <td>{{ book.ISBN }}</td>
              <td><button class="btn btn-danger btn-sm" @click="$emit('remove-from-wishlist', book.ISBN)">Remove</button></td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Wishlist',
    props: {
      wishlist: {
        type: Array,
        required: true
      },
      showWishlist: {
        type: Boolean,
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