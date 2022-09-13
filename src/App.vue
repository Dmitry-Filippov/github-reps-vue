<template>
  <div class="app">
    <Form></Form>

  </div>
</template>

<script>
import Form from './components/Form.vue';

export default {
  name: 'App',
  components: {
    Form,
  }
}
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
