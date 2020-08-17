<template>
  <div class="container">
    <div>
      <Logo />
      <h1>Мои сайты</h1>
      <div>
        <div v-for="title in titles" :key="title.site">
          <p>Название сайта:{{ title.site }}</p>

          <input type="text" value="jjlkslk" disabled />
          <nuxt-link to="/verify">Не подтвержден</nuxt-link>
          <br />
        </div>
        <div>
          <form action>
            <div>
              <p>Запуск проверки</p>
              <select>
                <option>Один раз</option>
                <option>Каждый день</option>
                <option>Раз в неделю</option>
                <option>Раз в месяц</option>
              </select>
              <p>Дата запуска</p>
              <input type="date" />
              <p>Время запуска</p>
              <input type="time" />
            </div>
          </form>
          <p>
            Статус
            <nuxt-link to="#">Запущено</nuxt-link>
          </p>
          <br />
          <div>
            <nuxt-link to="/scanReport">Отчетов о сканировании:</nuxt-link>
            <nuxt-link to="#">Удалить сайт</nuxt-link>
          </div>
        </div>

        <br />
        <nuxt-link to="/addSite">Добавить сайт</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      titles: [{ site: '1' }, { site: '2' }],
      items: [{ url: 'url/url' }, { url: 'url/url2' }],
    };
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  /* align-items: center; */
  /* text-align: center; */
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue',
    Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
