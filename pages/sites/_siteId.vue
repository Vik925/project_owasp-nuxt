<template>
  <section>
    <div class="container2">
      <div>
        <Logo />
        <h1>{{$route.params.siteId}} Подтверждение прав владения сайтом</h1>
        <div>
          <h2>Сайт - владелец не подтвержден</h2>
          <p>
            Прежде, чем получить возможность сканирования сайта на уязвимости, Вам необходимо подтвердить, что вы владеете
            данным сайтом. Мы можем предложить два способа подтверждения.
          </p>
          <div>
            <p>IN TXT "b30afe3d55fca7ad863115ab7d67f2b18fd344902a40c9f65b0c5ba5e214b274"</p>
          </div>
          <div>
            <br />
            <p>Второй способ: создайте файл в каталоге веб-сервера</p>
            <p>/verify/b30afe3d55fca7ad863115ab7d67f2b18fd344902a40c9f65b0c5ba5e214b274.html</p>
            <div>
              <button @on:click="verifySite">Подтвердить</button>
              <nuxt-link to="/">Вернуться назад</nuxt-link>
            </div>
            <div></div>
          </div>
        </div>
      </div>
    </div>
  </section>
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
          siteId: 1,
        },
        {
          title: 'ServicePipe2',
          url: 'https://servicepipe.ru2',
          status: false,
          scanReports: 0,
          siteId: 2,
        },
      ],
    };
  },
  methods: {
    verifySite() {
      axios
        .get('https://cors-anywhere.herokuapp.com/https://servicepipe.ru/')
        .then(rightsVerified => {
          console.log('Права доступа подтврждены');
        })
        .catch(rightNotVerified => {
          console.log('Права доступа не подтверждены');
        });
    },
  },
};
</script>

<style>
.container2 {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  /* align-items: center; */
  text-align: center;
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

db.webSites.insertOne({
  "title": "топпенопласт",
  "url": "https://servicepipe.ru2",
   "status": "true",
    "scanReports": 0
})
