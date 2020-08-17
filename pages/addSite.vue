<template>
  <div class="container">
    <div>
      <Logo />
      <h1>Добавить сайт</h1>
      <div>
        <form method="post" @submit.prevent="siteAdded">
          <p>Адрес сайта</p>
          <input type="text" v-model="post.title" />
          <p>Название сайта</p>
          <input type="text" v-model="post.urlSite" />
          <button type="submit">Добавить сайт</button>
        </form>
        <nuxt-link to="/">Вернуться назад</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      post: {
        title: '',
        urlSite: '',
      },
    };
  },

  methods: {
    async siteAdded() {
      const postNewSite = await axios({
        method: 'post',
        url: '/addSite',
        dataSite: {
          title: this.post.title,
          laurlSite: this.post.urlSite,
        },
      });
      const dataNewSite = postNewSite.config.dataSite;
      console.log(dataNewSite);
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