<template>
  <div class="container">
    <div>
      <Logo />
      <a-layout id="components-layout-demo-side" style="min-height: 75vh" class="radius">
        <a-layout-content style="margin: 0 16px">
          <a-breadcrumb style="margin: 16px 0">
            <h1>Подтверждение прав владения сайтом</h1>
          </a-breadcrumb>
          <a-card class="radius">
            <h3>Сайт {{ $route.params.id }} - владелец</h3>

            <p>
              Прежде, чем получить возможность сканирования сайта на уязвимости,<br />
              Вам необходимо подтвердить, что вы владеете данным сайтом. Мы можем предложить два способа подтверждения.
            </p>
            <div class="container2">
              <div class="row">
                <div class="column">
                  <a-steps :current="false" size="small">
                    <a-step title="Первый способ">
                      <a-icon slot="icon" type="check-circle" />
                    </a-step>
                  </a-steps>
                  <p>
                    Добавьте TXT запись в DNS <br />
                    IN TXT <b> ""</b>
                  </p>
                </div>
                <div class="column">
                  <a-steps :current="true" size="small">
                    <a-step title="Второй способ">
                      <a-icon slot="icon" type="check-circle" />
                    </a-step>
                  </a-steps>
                  <p>
                    Создайте файл в каталоге веб-сервера <br />
                    <b>/verify/.html </b>
                  </p>
                </div>
              </div>

              <a-button type="primary" v-on:click="verifySite">Подтвердить</a-button>
            </div>
          </a-card>
          <nuxt-link to="/">Вернуться назад</nuxt-link>
        </a-layout-content>
      </a-layout>
    </div>
  </div>
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

<style scoped>
  .container2 {
    /* margin: 0 auto; */
    /* min-height: 100vh; */
    text-align: center;
    margin-left: auto;
    margin-right: auto;
  }

  button {
    width: 200px;
  }

  @media (max-width: 570.98px) {
    button {
      width: 100%;
    }
  }

  .row:before,
  .row:after {
    content: ' ';
    display: table;
  }
  .row:after {
    clear: both;
  }

  .column {
    position: relative;
    float: left;
    padding: 10px 10px;
    width: 50%;
  }

  .column-1 {
    width: 6.86666666667%;
  }
  .column-2 {
    width: 15.3333333333%;
  }
  .column-3 {
    width: 23.8%;
  }
  .column-4 {
    width: 32.2666666667%;
  }
  .column-5 {
    width: 40.7333333333%;
  }
  .column-6 {
    width: 49.2%;
  }
  .column-7 {
    width: 57.6666666667%;
  }
  .column-8 {
    width: 66.1333333333%;
  }
  .column-9 {
    width: 74.6%;
  }
  .column-10 {
    width: 83.0666666667%;
  }
  .column-11 {
    width: 91.5333333333%;
  }
  .column-12 {
    width: 100%;
  }

  @media only screen and (max-width: 550px) {
    .column-1,
    .column-2,
    .column-3,
    .column-4,
    .column-5,
    .column-6,
    .column-7,
    .column-8,
    .column-9,
    .column-10,
    .column-11,
    .column-12 {
      width: auto;
      float: none;
    }
  }

  .ant-steps {
  }
</style>
