<template>
  <section>
    <div class="container2">
      <div>
        <Logo />
        <h1>Подтверждение прав владения сайтом</h1>
        <div>
          <h2>Сайт {{$route.params.id}} - владелец не подтвержден</h2>
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
              <button>Подтвердить</button>
            </div>
            <div></div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>