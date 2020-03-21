<template>
  <form v-on:submit.prevent="bookSubmit(bookTitle, bookAuthor)" class="" action="#" method="post">
    <input v-model="bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model="bookAuthor" type="text" name="author" value="" placeholder="Book Author">
    <div>
      <input v-model="bookData.finishedReading" type="checkbox">
      <label for="finishedReading">Finished Reading</label>
      <input v-model="bookData.ownership" value="borrowed" type="radio">
      <label for="borrowed">borrowed</label>
      <input v-model="bookData.ownership" value="bought" type="radio">
      <label for="bought">bought</label>
    </div>
    <button type="submit" name="button">Add Book</button>
  </form>
</template>

<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
      bookData: {
        bookTitle: "",
        bookAuthor: "",
        finishedReading: false,
        ownership: []
      }
    };
  },
  methods: {
    bookSubmit(bookData, bookSubmit) {
      this.$emit("addBook", bookData, bookSubmit);
    }
  }
};
</script>

<style>
</style>
