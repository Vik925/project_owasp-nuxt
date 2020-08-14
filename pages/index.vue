<template>
  <div class="container">
    <div>
      <Logo />
      <h1>Мои сайты</h1>
      <div>
        <div>
          <p>Название сайта:</p>
          <input type="text" />
          <a href="/verify">Не подтвержден</a><br />
        </div>
        <form action="">
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
        <p>Статус <a href="#">Запущено</a></p>
        <br />
        <div>
          <a href="/scanReport">Отчетов о сканировании:</a>
          <a href="#">Удалить сайт</a>
        </div>
        <br />
        <a href="/addSite">Добавить сайт</a>
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
