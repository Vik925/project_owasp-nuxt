<template>
  <div class="container">
    <div>
      <Logo />
      <h1>Добавить сайт</h1>
      <div>
        <form method="post" @submit.prevent="siteAdded">
          <p>Адрес сайта</p>
          <input v-model="post.titleWebSite" />
          <p>Название сайта</p>
          <input v-model="post.urlWebSite" />
          <button type="submit">Добавить сайт</button>
        </form>
        <nuxt-link to="/">Вернуться назад</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        post: {
          titleWebSite: '',
          urlWebSite: '',
        },
      };
    },

    methods: {
      async siteAdded() {
        try {
          // ошибка на сервере не передалась тебе :(
          //  ⚡ [ERROR]: [Modules] :: Error: || 404 • Not Found • |body| not found

          const url = 'http://185.79.117.244:4004/api/modules/scanner/send';
          const payload = {
            websiteTitle: this.post.titleWebSite,
            websiteUrl: this.post.urlWebSite,
          };

          const answer = await this.$axios({
            url,
            method: 'POST',
            data: payload,
            validateStatus: false,
          });
          // console.log('answer', answer);
          const { data } = answer;
          if (data.statusCode !== 200 && data.statusCode !== 201) throw new Error(data.serverAnswer);

          const result = data.serverAnswer;
          console.log('result', result);

          return result;
        } catch (err) {
          console.error(`❌ [ERROR] ${err}`);
          return err;
        }
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
