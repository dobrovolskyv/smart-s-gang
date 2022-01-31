<template>
  <main class="main yellow lighten-5">
    <div class="container">
      <div v-if="beer.length <= 0" class="progress">
        <div class="indeterminate"></div>
      </div>
      <div class="user" v-else>
        <h3 class="user__title">Твое бухлишко на сегодня:</h3>
        <ul>
          <li class="user__item">Бренд: {{ beer.brand }}</li>
          <li class="user__item">Название: {{ beer.name }}</li>
          <li class="user__item">Горечь: {{ beer.ibu }}</li>
          <li class="user__item">Стиль: {{ beer.style }}</li>
          <li class="user__item">Солод: {{ beer.malts }}</li>
          <li class="user__item">Градус: {{ beer.alcohol }}</li>
          <li class="user__item">Дрожжи: {{ beer.yeast }}</li>
        </ul>
      </div>

      <button class="btn" @click="getRandomBeer">Испытать удачу</button>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      beer: {},
    };
  },
  mounted() {
    this.getRandomBeer();
  },
  methods: {
    async getRandomBeer() {
      try {
        const response = await fetch(
          "https://random-data-api.com/api/beer/random_beer"
        );
        this.beer = await response.json();
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>
.main {
  width: 50%;
}
.user__title {
  font-size: 32px;
  margin-top: 10px;
}
.user__item {
  font-size: 20px;
  line-height: 27px;
  margin-top: 15px;
}
.btn {
  margin: 50px 0;
}
@media (max-width: 768px) {
  .main {
    width: 100%;
  }
  .user__title {
    margin-top: 30px;
  }
}
</style>