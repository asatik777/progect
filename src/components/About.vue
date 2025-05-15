<template>
    <div class="about-container">
      <section class="intro1">
        <div class="intro1-content">
          <h1>О нас</h1>
          <p>
            Добро пожаловать в <strong>Британские пекарни</strong> – место, где традиции встречаются с качеством и вкусом!
          </p>
          <p>
            Мы — команда, объединившая людей, которые любят создавать и дарить людям моменты радости с помощью своей работы.
            Каждый продукт в нашей пекарне — это не просто еда, это история, вложенная в каждый ингредиент.
          </p>
        </div>
      </section>
      <section class="offerings">
        <h2>Что мы предлагаем</h2>
        <div class="offerings-list">
          <div class="offering-item">
            <img src="../assets/path_to_image_1.png" alt="Пирог" class="offering-image" />
            <h3>Пироги и торты</h3>
            <p>Идеальны для любого случая — от семейных праздников до уютных вечеров.</p>
          </div>
          <div class="offering-item">
            <img src="../assets/path_to_image_2.png" alt="Кексы и булочки" class="offering-image" />
            <h3>Кексы и булочки</h3>
            <p>Прекрасный выбор для утреннего кофе и заряд энергии на весь день.</p>
          </div>
          <div class="offering-item">
            <img src="../assets/path_to_image_3.png" alt="Шоколадные изделия" class="offering-image" />
            <h3>Шоколадные изделия и конфеты</h3>
            <p>Идеальны для сладких моментов и подарков.</p>
          </div>
        </div>
      </section>
      <section class="mission">
                <h2>Наша команда</h2>
        <p>
          Мы — это не просто пекари и кондитеры. Мы — настоящие энтузиасты своего дела. За каждым изделием стоит целая команда людей,
          стремящихся сделать вашу жизнь вкуснее.
        </p>
        <h2>Наша миссия</h2>
        <p>
          Мы верим в качество и честность. Наши продукты сделаны с любовью и уважением к клиентам. Мы используем только лучшие ингредиенты,
          тщательно отбирая их, чтобы каждый ваш визит к нам приносил настоящее наслаждение.
          
        </p>
        <h2>Наши традиции</h2>
        <p>
          Вдохновленные британской кулинарной традицией, мы с гордостью представляем вам выпечку, созданную по старинным рецептам, но с
          учетом современных технологий и стандартов качества.
        </p>
        <h2>Будьте с нами!</h2>
        <p>
          Мы приглашаем вас стать частью нашей большой семьи! Загляните к нам в магазин или закажите любимые угощения онлайн — мы
          всегда рады новым гостям и будем счастливы, если наша выпечка станет неотъемлемой частью вашего дня.
        </p>

      </section>
    </div>
  </template>
  
  <script>
  export default {
    name: "AboutPage",
  };
  </script>
  
  <style scoped>
  .about-container {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    margin: 0 auto;
    padding: 20px;
    max-width: 1200px;
  }
  
  h1, h2 {
    color: #333;
  }
  
  h2 {
    margin-top: 40px;
    font-size: 2rem;
  }
  
  .intro1-content p {
    font-size: 1.1rem;
    margin: 20px 0;
  }
  
  .intro1-content h1 {
    font-size: 2.5rem;
    margin-bottom: 10px;
  }
  
  .offerings-list {
    display: flex;
    justify-content: space-between;
    margin-top: 30px;
  }
  
  .offering-item {
    width: 30%;
    text-align: center;
    padding: 10px;
  }
  
  .offering-item img {
    width: 100%;
    height: auto;
    border-radius: 8px;
    transition: transform 0.3s ease;
  }
  
  .offering-item img:hover {
    transform: scale(1.05);
  }
  
  .team p, .invitation1 p {
    font-size: 1.1rem;
    margin-top: 10px;
  }
  
  .invitation1 {
    background-color: #ffffff;
    padding: 20px;
    border-radius: 8px;
    margin-top: 40px;
    text-align: center;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .invitation1 h2 {
    font-size: 2rem;
    color: #333;
  }
  
  .intro1, .mission, .traditions, .team {
    margin-bottom: 40px;
  }
  
  .intro1 {
    background-color: #ffffff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  
  .mission, .traditions {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  </style>
  