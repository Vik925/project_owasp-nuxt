<template>
  <div class="container">
    <div>
      <Logo />
      <h1>Подтверждение прав владения сайтом</h1>
      <div>
        <h2>Сайт https://www.toppenoplast.ru/ - владелец не подтвержден</h2>
        <p>
          Прежде, чем получить возможность сканирования сайта на уязвимости, Вам необходимо подтвердить, что вы владеете
          данным сайтом. Мы можем предложить два способа подтверждения.
        </p>
        <div>
          <p></p>
          <p>IN TXT "b30afe3d55fca7ad863115ab7d67f2b18fd344902a40c9f65b0c5ba5e214b274"</p>
          <button>Подтвердить</button>
        </div>
        <div>
          <p>Второй способ: создайте файл в каталоге веб-сервера</p>
          <p>/verify/b30afe3d55fca7ad863115ab7d67f2b18fd344902a40c9f65b0c5ba5e214b274.html</p>
          <button>Подтвердить</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {};
</script>

<style>
  .container {
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
