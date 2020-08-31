<template>
  <div class="container">
    <div>
      <Logo />
      <h1>Мои сайты</h1>

      <div v-for="(site, index) of sites" :key="index">
        <br />
        <form action>
          <p>{{ index + 1 }}</p>
          <p>Название сайта: {{ site.websiteTitle }}</p>
          <p>URL сайта: {{ site.websiteUrl }}</p>
          <div v-if="site.status">
            <button>Запустить проверку</button>
            <br />
            <div>
              <nuxt-link to="/scanReport">Отчетов о сканировании: {{ site.scanReports }}</nuxt-link>
            </div>
          </div>
          <div v-else>
            <a href="#" @click.prevent="openSiteVerify(index + 1)">Не подтвержден</a>
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
      <p @click="getSites">dddd {{ sites }}</p>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        sites: [{ createdAt: '', scanReports: '', status: '', websiteTitle: '', websiteUrl: '', _id: '' }],
      };
    },
    methods: {
      async getSites() {
        try {
          const url = 'http://185.79.117.244:4004/api/modules/scanner/info';
          const payload = {
            target: '5f46a2d7db855f065ccd8dc6', // по юзеру
          };

          const answer = await this.$axios({
            url,
            method: 'POST',
            data: payload,
            validateStatus: false,
          });
          console.log('answer', answer);
          const { data } = answer;
          if (data.statusCode !== 200 && data.statusCode !== 201) throw new Error(data.serverAnswer);

          const result = data.serverAnswer;
          this.sites = result;
          console.log('result', result);

          return result;
        } catch (err) {
          console.error(`❌ [ERROR] ${err}`);
          return err;
        }
      },
      openSiteVerify(index) {
        this.$router.push(`/verify/${index}`);
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
