<template>
  <div id="app" class="app">
    <!-- heading -->
    <header class="app__heading">
      <h1>Books<span>.app</span></h1>
    </header>

    <!-- books list -->
    <books-list :books="books" @remove="removeBook"/>

    <!-- no books message -->
    <books-length-msg :length="books.length" />
    <!-- add book form -->
    <book-form @add="addBook" />
    <!-- add book summary -->
    <books-summary :length="books.length" :books="books"/>
  </div>
</template>

<script>
import BooksList from './components/BooksList'
import BooksLengthMsg from './components/BooksLengthMsg'
import BookForm from './components/BookForm'
import BooksSummary from './components/BooksSummary'

export default {
  name: 'App',
  data: () => ({
    books: [
      {
        title: 'The Catcher in the Rye',
        price: 20
      },
      {
        title: 'Of Mice and Men',
        price: 18
      }]
  }),
  components: { BooksList, BooksLengthMsg, BookForm, BooksSummary },
  methods: {
    addBook (book) {
      this.books.push({ ...book })
    },
    removeBook (index) {
      this.books.splice(index, 1)
    }
  }
}
</script>

<style lang="scss">
.app {
  width: 100%;
  max-width: 1000px;
  padding: 2rem;
  margin: 0 auto;

  &__heading {
    font-size: 3rem;
    text-align: center;
    span {
      color: #5a58da;
    }
  }
}
</style>
