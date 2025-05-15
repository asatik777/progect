<template>
  <section class="bakeries">
    <h2>Наши пекарни</h2>

    <div class="bakery-section">
      <h3>История создания</h3>
      <p>
        Всё началось с маленькой семейной кухни, где выпечка была частью нашей души. Со временем наша любовь к ремеслу превратилась в первую пекарню. Сегодня мы гордимся тем, что сохранили тёплую атмосферу домашнего уюта в каждом уголке наших заведений.
      </p>
      <img src="../assets/history.png" alt="История пекарни" class="bakery-image" />
    </div>

    <div class="bakery-section">
      <h3>Сотрудничество</h3>
      <p>
        Мы сотрудничаем с местными фермерами, чтобы привозить свежие и натуральные продукты. Наши партнёры — это проверенные временем поставщики, благодаря которым мы уверены в качестве каждого ингредиента.
      </p>
      <img src="../assets/partners.png" alt="Сотрудничество" class="bakery-image" />
    </div>

    <div class="map-section">
      <h3>Вы можете найти нас тут</h3>
      <iframe
        src="https://yandex.ru/map-widget/v1/?um=constructor%3Ae59ee101b8cdd4e40503d9f3a723c8a376bb578c86efb2a8b2ac178315f92cd1&amp;source=constructor"
        width="100%"
        height="400"
        frameborder="0"
      ></iframe>
    </div>
  </section>
</template>

<style scoped>
.bakeries {
  padding: 40px 20px;
  max-width: 1200px;
  margin: 0 auto;
}

h2 {
  font-size: 2.2rem;
  margin-bottom: 30px;
  text-align: center;
  color: #7c4d0f;
}

.bakery-section {
  margin-bottom: 40px;
}

.bakery-section h3 {
  color: #b65b15;
  margin-bottom: 10px;
  font-size: 1.5rem;
}

.bakery-section p {
  font-size: 1rem;
  line-height: 1.6;
  color: #444;
  margin-bottom: 15px;
}

.bakery-image {
  max-width: 100%;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

.map-section {
  margin-top: 50px;
}

.map-section h3 {
  margin-bottom: 15px;
  font-size: 1.5rem;
  color: #6d3e07;
}
</style>
