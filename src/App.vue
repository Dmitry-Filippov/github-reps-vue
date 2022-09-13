<template>
  <div class="app">
    <Form v-bind:search="this.search" v-bind:isLoading="this.isLoading"></Form>
    <Results :results="this.results" :totalCount="this.totalCount" />
    <ErrorPopUp
      :closePopUp="this.closePopUp"
      :isPopUpOpen="this.isPopUpOpen"
      :error="this.error"
    />
  </div>
</template>

<script>
import { searchReps } from "./api/api";
import Form from "./components/Form.vue";
import Results from "./components/Results.vue";
import ErrorPopUp from "./components/ErrorPopUp.vue";

export default {
  name: "App",
  components: {
    Form,
    Results,
    ErrorPopUp,
  },

  data: function () {
    return {
      results: [],
      totalCount: 0,
      isLoading: false,
      isPopUpOpen: false,
      error: {},
    };
  },

  methods: {
    search(searchWord) {
      this.isLoading = true;
      searchReps(searchWord)
        .then((res) => {
          this.totalCount = res.total_count;
          this.results = res.items.slice(0, 10);
        })
        .then(() => {
          this.isLoading = false;
        })
        .catch((err) => {
          this.error = err;
          this.isLoading = false;
          this.isPopUpOpen = true;
        });
    },

    closePopUp() {
      this.isPopUpOpen = false;
    },
  },
};
</script>

<style>
/* font */
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500&display=swap");

/* reset */
h1,
h2,
h3,
p,
input,
form,
button,
ul,
li,
a {
  margin: 0;
  padding: 0;
  border: none;
  background: none;
  box-sizing: border-box;
  text-decoration: none;
}

body {
  font-family: "Roboto", sans-serif;
  color: #fff;
  background-color: #262626;
}

.app {
  width: 800px;
  max-width: 80%;
  margin: 0 auto;
  padding-top: 30px;
  padding-bottom: 50px;
}
</style>
