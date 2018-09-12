
<template>
  <div id="app">
    <div class="main">
      <div class="logo-text">
        <div class="logo"><h1> GALVANIZE READS</h1></div>
        <h3>FIND YOUR BOOKS HERE</h3>
        <select v-model="selected" :required="true">
          <option :value=null>Select Options</option>
          <option v-for='booksObject in books'
            v-bind:value='booksObject.id'
            :key='booksObject.id'
            >{{booksObject.id}}
          </option>
        </select>
    </div>
    <!-- <div class="cardList">
      <authors v-for='authFirst in queriedAuthors.id' :authFirst='id.authFirst.authLast' :authBio='id.authBio' />
    </div> -->
  </div>
  <div class="footer">
    <Footer />
  </div>
  </div>

</template>

<script>

import books from './components/books.vue'
import authors from './components/authors.vue'

export default {
  name: "App",
  components: {
    authors,
    books
  },

  data() {
    return {
      currentBook: "",
      books: []      
    }
  },

  computed: {
    selected: {
      get() {
        return null;
      },
      set(optionValue) {
        this.currentBook = optionValue;

        fetch ("https://galvaniizereads.herokuapp.com/books" + optionValue)
          .then(resp => resp.json())
          .then(resp => {
            this.queriedBooks = resp;
          })
      }
    }
  },

  methods: {
    populateBooks() {
      fetch("https://galvaniizereads.herokuapp.com/books")
        .then(resp => resp.json())
        .then(resp => {
          this.books = resp
        })
    }
  },

  mounted() {
    this.populateBooks()
  }
}


</script>


// 3. Create the router instance and pass the `routes` option
// You can pass in additional options here, but let's
// keep it simple for now.
const router = new VueRouter({
  routes // short for `routes: routes`
})

// 4. Create and mount the root instance.
// Make sure to inject the router with the router option to make the
// whole app router-aware.
const app = new Vue({
  router
}).$mount('#app')

// Now the app has started!



<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.books-author {
display: flex;
flex-direction: row;

}

.books {
display: flex;
border: 2px solid black;
  color:pink;
}

.authors {
  display: flex;
border: 2px solid black;
  color: red;
}

</style>


