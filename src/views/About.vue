<template>
  <div id="about">
    <div v-show=loading>
      <div class="book">
        <div class="book__page"></div>
        <div class="book__page"></div>
        <div class="book__page"></div>
      </div>
    </div>
    <div v-show="!loading">
      <h1>This is an about page</h1>
      Main Contents
    </div>
  </div>
</template>

<script>
export default {
  el: "#about",
  data() {
    return{
      loading: true
    }
  },
  mounted() {
    setTimeout(() => {
      this.loading = false;
    }, 6000);
  }
}
</script>

<style>
  
</style>