<template>
  <div>
    <book
      :key="book.id" v-for="book in books" :book="book"
      @toggle-reminder="$emit('toggle-reminder', book.id)"
      @delete-book="$emit('delete-book', book.id)"
    />
  </div>
</template>

<script>
import book from './book'

export default {
  name: 'books',
  props: {
    books: Array,
  },
  components: {
    book
    
  },
  emits: ['delete-task', 'toggle-reminder'],
}
</script>

