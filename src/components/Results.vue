<template>
  <div class="results" v-if="this.results.length > 0">
    <h2 class="results__title">Совпадения:</h2>
    <ul class="results__results-list">
      <li v-for="item in results" :key="item.id" class="result-item">
        <h3 class="result-item__name">
          <a :href="item.html_url" target="blank">
            {{ item.name }}
          </a>
        </h3>
        <p class="result-item__owner">Владелец: {{ item.owner.login }}</p>
        <p class="result-item__lang">
          Язык разработки: {{ item.language ? item.language : "Не указан" }}
        </p>
      </li>
    </ul>
    <p class="results__all">
      Всего репозиториев найдено: {{ this.totalCount }}
    </p>
  </div>
</template>


<script>
export default {
  name: "ResultsComponent",
  props: {
    results: Array,
    totalCount: Number,
  },
};
</script>

<style>
.result-item {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
  padding: 15px 0;
}

.result-item__name a {
  font-weight: 500;
  font-size: 30px;
  color: rgb(109, 214, 235);
}

.result-item__owner {
  font-size: 20px;
  font-weight: 300;
  padding-top: 4px;
}

.result-item__lang {
  font-size: 20px;
  font-weight: 400;
  padding-top: 4px;
}

@media screen and (max-width: 1020px) {
  .result-item__name a {
    font-size: 25px;
  }

  .result-item__owner,
  .result-item__lang {
    font-size: 17px;
  }
}

.results {
  padding-top: 50px;
}

.results__title {
  font-size: 50px;
  font-weight: 500;
  line-height: 1.5em;
}

.results__results-list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding-top: 10px;
}

.results__all {
  padding-top: 30px;
  font-size: 30px;
  font-weight: 400;
  line-height: 1.5em;
  text-align: left;
}

@media screen and (max-width: 1020px) {
  .results__title {
    text-align: center;
    font-size: 40px;
  }

  .results__results-list {
    grid-template-columns: 1fr;
  }

  .results__all {
    font-size: 20px;
  }
}
</style>