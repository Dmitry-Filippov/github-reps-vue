<template>
  <div class="form">
    <h1 class="form__title">Поиск на GitHub</h1>
    <form class="form__form" v-on:submit="this.handleFormSubmit">
      <label for="input" class="form__label"> Введите ключевое слово </label>
      <input
        type="text"
        required
        name="input"
        v-model="inputValue"
        v-bind:class="`form__input ${
          isLoading ? 'form__input_mob-hidden' : ''
        }`"
      />
      <button
        v-bind:class="`form__submit ${
          isLoading ? 'form__submit_mob-hidden' : ''
        }`"
      >
        Поиск
      </button>
      <div
        v-bind:class="`form__loader ${isLoading ? 'form__loader_active' : ''} `"
      >
        <Loader />
      </div>
    </form>
  </div>
</template>

<script>
import Loader from "./Loader.vue";
export default {
  name: "FormComponent",
  props: {
    search: Function,
    isLoading: Boolean,
  },
  data: () => {
    return {
      inputValue: "",
    };
  },
  methods: {
    handleFormSubmit: function (event) {
      event.preventDefault();
      this.search(this.inputValue);
    },
  },
  components: { Loader },
};
</script>

<style>
.form__title {
  font-weight: 500;
  font-size: 70px;
  line-height: 1.5em;
}

.form__form {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
}

.form__label {
  font-size: 30px;
  font-weight: 400;
}

.form__input {
  font-weight: 300;
  font-size: 20px;
  outline: none;
  border: 1px solid #696969;
  border-radius: 5px;
  padding: 10px;
  width: 300px;
  color: #fff;
}

.form__submit {
  padding: 10px;
  font-weight: 300;
  font-size: 20px;
  border-radius: 5px;
  color: #fff;
  text-align: center;
  border: 1px solid #696969;
  cursor: pointer;
}

.form__loader {
  position: absolute;
  right: -90px;
  top: -20px;
  display: none;
}

.form__loader_active {
  display: block;
}

@media screen and (max-width: 1020px) {
  .form__title {
    text-align: center;
    font-size: 40px;
  }

  .form__form {
    flex-direction: column;
    min-height: 135px;
  }

  .form__label {
    font-size: 20px;
  }

  .form__input {
    margin-top: 20px;
    font-size: 15px;
    padding: 7px;
  }

  .form__input_mob-hidden {
    display: none;
  }

  .form__submit {
    margin-top: 15px;
    font-size: 15px;
    padding: 7px;
  }

  .form__submit_mob-hidden {
    display: none;
  }

  .form__loader {
    position: static;
  }
}
</style>