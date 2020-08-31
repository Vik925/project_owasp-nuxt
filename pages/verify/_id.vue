<template>
  <section>
    <div class="container2">
      <div>
        <Logo />
        <h1>Подтверждение прав владения сайтом</h1>
        <div>
          <h2>Сайт {{ $route.params.id }} - владелец</h2>
          <p>
            Прежде, чем получить возможность сканирования сайта на уязвимости, Вам необходимо подтвердить, что вы
            владеете данным сайтом. Мы можем предложить два способа подтверждения.
          </p>
          <p>Ваш ключ веритификации: <b></b></p>
          <br />
          <div>
            <p>Первый способ: добавьте TXT запись в DNS</p>
            <p>IN TXT <b> ""</b></p>
          </div>
          <div>
            <br />
            <p>Второй способ: создайте файл в каталоге веб-сервера</p>
            <p>
              <b>/verify/.html </b>
            </p>
            <div>
              <br />
              <button v-on:click="verifySite">Подтвердить</button>
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
  export default {
    data() {
      return {
        status: '',
      };
    },
    methods: {
      async verifySite() {
        try {
          const url = '/api/modules/scanner/exist-url';
          const payload = {
            www: 'https://www.toppenoplast.ru123123/',
          };

          const answer = await this.$axios({
            url: `${this.$serverAPI}${url}`,
            method: 'POST',
            data: payload,
            validateStatus: false,
          });

          console.log('answer', answer);
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
      validate({ params }) {
        return /^\d+$/.test(params.id);
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
