<template>
  <div class="container">
    <div>
      <Logo />
      <h1>Мои сайты</h1>

      <div v-for="site in sites" :key="site">
        <br />
        <form action>
          <p>Название сайта: {{ site.title }}</p>
          <p>URL сайта: {{ site.url}}</p>
          <div v-if="site.status">
            <button>Запустить проверку</button>
            <br />
            <div>
              <nuxt-link to="/scanReport">Отчетов о сканировании: {{site.scanReports}}</nuxt-link>
            </div>
          </div>
          <div v-else>
            <a href="#" @click.prevent="openSiteVerify(site.id)">Не подтвержден</a>
          </div>
        </form>
        <nuxt-link to="#">Удалить сайт</nuxt-link>
      </div>

      <!-- <div>
         
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
      </div>-->

      <br />
      <nuxt-link to="/addSite">Добавить сайт</nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      sites: [
        {
          title: 'ServicePipe',
          url: 'https://servicepipe.ru',
          status: true,
          scanReports: 1,
          id: 1,
        },
        {
          title: 'ServicePipe2',
          url: 'https://servicepipe.ru2',
          status: false,
          scanReports: 0,
          id: 2,
        },
      ],
    };
  },
  methods: {
    openSiteVerify(site) {
      this.$router.push('/sites/' + site);
    },
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
