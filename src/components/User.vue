<template>
  <header class="header amber lighten-2">
    <div class="container">
      <h1 class="header__title">Личный кабинет алкозавра</h1>
      <div v-if="users.length <= 0" class="progress">
        <div class="indeterminate"></div>
      </div>
      <div v-else class="header__inner">
        <img :src="users.avatar" alt="" />
        <ul class="info__list">
          <li class="info__item">
            Имя: <span class="info__span">{{ users.first_name }}</span>
          </li>
          <li class="info__item">
            Фамилия: <span class="info__span">{{ users.last_name }}</span>
          </li>
          <li class="info__item">
            Пол: <span class="info__span">{{ users.gender }}</span>
          </li>
          <li class="info__item">
            Дата рождения:
            <span class="info__span">{{ users.date_of_birth }}</span>
          </li>
          <li class="info__item">
            Погоняло: <span class="info__span">{{ users.username }}</span>
          </li>
          <li class="info__item">
            Электронная почта: <span class="info__span">{{ users.email }}</span>
          </li>
          <li class="info__item">
            Телефон: <span class="info__span">{{ users.phone_number }}</span>
          </li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      users: {},
    };
  },
  mounted() {
    this.getRandomUser();
  },
  methods: {
    async getRandomUser() {
      try {
        const response = await fetch(
          "https://random-data-api.com/api/users/random_user"
        );
        this.users = await response.json();
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>
.header {
  padding: 1px;
  width: 50%;
}
.header__title {
  font-size: 32px;
  margin-top: 10px;
}
.header__inner {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.header__inner img {
  width: 50%;
  margin-right: 50px;
}
.info__item {
  margin-top: 15px;
}
.info__span {
  font-weight: 700;
  font-size: 20px;
}
@media (max-width: 768px) {
  .header {
    width: 100%;
  }
}
</style>