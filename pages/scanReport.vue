<template>
  <div class="container">
    <div>
      <Logo />
      <h1>Отчет о сканировании</h1>
      <div>
        <p>Название сайта</p>
        <div>
          <p>Дата запуска</p>
          <p>Время запуска</p>
          <p>Статус</p>
          <br />
          <table>
            <tbody>
              <tr>
                <th>Обнаружено уязвимостей</th>
              </tr>
              <tr>
                <th>High</th>
                <th>Medium</th>
                <th>Low</th>
                <th>Info</th>
              </tr>
              <tr>
                <td>44</td>
                <td>55</td>
                <td>66</td>
                <td>77</td>
              </tr>
            </tbody>
          </table>
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
