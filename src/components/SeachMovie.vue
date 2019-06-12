<template>
  <div id="search">
    <div class="input-group">
      <input type="text" class="form-control" placeholder="Type name of movie..." v-model="title">
      <span class="input-group-btn">
        <button class="btn btn-search form-control" type="button" :disabled="title.length <3" @click="searchMovie">
          <i class="fas fa-search"></i> Search
        </button>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "searchMovie",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    searchMovie() {
      this.$emit('searchMovie', this.title);
      this.title = "";
    }
  }
};
</script>

<style scoped>
#search{
    padding-top: 50px;
    padding-bottom: 20px;
}
</style>
