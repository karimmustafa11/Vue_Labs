<template>
  <div id="mainapp" class="container my-4">
    <h1 class="mb-4">Vue JS Lab One</h1>
    <BookList />
    <BookCards :books="books" @add-to-wishlist="addToWishlist" />
    <Wishlist 
      :wishlist="wishlist" 
      :show-wishlist="showWishlist" 
      @toggle-wishlist="toggleWishlist"
      @remove-from-wishlist="removeFromWishlist"
    />
  </div>
</template>

<script>
import BookList from './components/BookList.vue'
import BookCards from './components/BookCards.vue'
import Wishlist from './components/Wishlist.vue'
import books from './data/books.js'

export default {
  name: 'App',
  components: {
    BookList,
    BookCards,
    Wishlist
  },
  data() {
    return {
      books: books,
      wishlist: [],
      showWishlist: false
    }
  },
  methods: {
    addToWishlist(book) {
      if (!this.wishlist.find(b => b.ISBN === book.ISBN)) {
        this.wishlist.push(book);
      }
    },
    removeFromWishlist(isbn) {
      this.wishlist = this.wishlist.filter(b => b.ISBN !== isbn);
    },
    toggleWishlist() {
      this.showWishlist = !this.showWishlist;
    },
    formatPrice(price) {
      return new Intl.NumberFormat('ar-SA', { style: 'currency', currency: 'EGP' }).format(price);
    }
  }
}
</script>