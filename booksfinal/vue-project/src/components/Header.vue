<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      v-show="homePage"
      @btn-click="$emit('toggle-add-book')"
      :text="showAddbook ? 'Close' : 'Add book'"
      :color="showAddbook ? 'red' : 'blue'"
    />
  </header>
</template>

<script>
import Button from './Button'

export default {
    name:'Header',  
    props: {
    title: String,
    showAddbook: Boolean,
  },  
   components: {
    Button,
  },    
}
</script>


<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
