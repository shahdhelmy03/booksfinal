<template>
  <div class="container">
    <Header @toggle-add-book="toggleAddbook"
    title="liabary"
    : showAddbook="showAddbook"/>
    <div v-show="showAddbook">
      <Addbook @add-book="addbook"/>
    </div>
    <books
    @toggle-reminder="toggleReminder"
    @delete-book="deletebook"
    :books="books"
    />
   
    </div>
</template>

<script>
import Header from './components/Header'
import books from './components/books'
import Addbook from './components/Addbook.vue'


export default {
  name: 'App',
  components: {
    Header,
    books,
    Addbook,

  },
  data() {
    return {
     books:[],
     showAddbook: false,
    }
  },
  methods: {
    toggleAddbook()
    {
      this.showAddbook= !this.showAddbook
    },
    addbook(book){
      this.books=[...this.books,book]
    },
    deletebook(id){
      if(confirm('are  you sure')){
        this.books = this.books.filter((book) => book.id
        !==id)

      }
    },
  toggleReminder(id){
    this.books=this.books.map((book) =>
       book.id=== id?{ ... book, reminder: !book.reminder} : task)  
    },
  }
}

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
