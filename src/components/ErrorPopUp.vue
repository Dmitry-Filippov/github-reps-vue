<template>
  <div
    :class="`pop-up ${this.isPopUpOpen ? 'pop-up_open' : ''}`"
    @click="this.handlePopUpClose"
  >
    <div className="pop-up__wrapper">
      <p className="pop-up__text">Произошла ошибка:</p>
      <p className="pop-up__text pop-up__err">{{ this.error.message }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ErrorPopUp",
  props: {
    error: Object,
    isPopUpOpen: Boolean,
    closePopUp: Function,
  },
  methods: {
    handlePopUpClose(e) {
      if (e.target.className === "pop-up pop-up_open") {
        this.closePopUp();
      }
    },
  },
};
</script>

<style>
.pop-up {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.631);
  display: none;
  align-items: center;
  justify-content: center;
}

.pop-up_open {
  display: flex;
}

.pop-up__wrapper {
  padding: 50px 100px;
  background-color: #fff;
  border-radius: 5px;
}

.pop-up__text {
  color: rgb(139, 0, 0);
  font-weight: 400;
  font-size: 40px;
  text-align: center;
}

.pop-up__err {
  padding-top: 30px;
}

@media screen and (max-width: 1020px) {
  .pop-up__wrapper {
    padding: 30px 60px;
  }

  .pop-up__text {
    font-size: 20px;
  }
}
</style>