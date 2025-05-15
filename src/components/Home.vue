<template>
    <div class="home">
      <!-- Видеофон с логотипом и названием -->
      <section class="hero">
        <video autoplay muted loop playsinline class="video-background">
          <source src="../assets/background.mp4.mp4" type="video/mp4" />
        </video>
  
        <div class="overlay">
          <img src="../assets/logo.png.png" alt="British Bakery Logo" class="overlay-logo" />
          <h2 class="overlay-title">Британские пекарни</h2>
          <p class="overlay-subtitle">Знаем толк в кулинарии и хлебопечении</p>
        </div>
      </section>
  
      <!-- Контент под видео -->
      <section class="hero-content">
        <div class="hero-text">
          <h1>Добро пожаловать в Британские пекарни!</h1>
          <p>Свежая, ароматная и настоящая выпечка каждый день.</p>
          <button @click="$emit('navigate', 'Menu')">Посмотреть меню</button>
        </div>
        <img src="../assets/123.webp" alt="Выпечка" class="hero-image" />
      </section>
  
      <!-- Преимущества -->
      <section class="features">
        <div class="feature">
          <h2>Натуральные ингредиенты</h2>
          <p>Мы используем только высококачественные продукты без добавок и консервантов.</p>
          <img src="../assets/ingredients.png" alt="Ингредиенты" class="feature-image" />
        </div>
        <div class="feature">
          <h2>Ручная работа</h2>
          <p>Каждое изделие — результат труда наших мастеров-пекарей.</p>
          <img src="../assets/handmade.png" alt="Ручная работа" class="feature-image" />
        </div>
        <div class="feature">
          <h2>Традиционные рецепты</h2>
          <p>Английские традиции, передающиеся из поколения в поколение.</p>
          <img src="../assets/tradition.png" alt="Традиции" class="feature-image" />
        </div>
      </section>
</div>
  </template>
  
  
  <script>
  export default {
    name: 'Home'
  }
  </script>
  
  <style scoped>
  .home {
    margin: 0;
    padding: 0;
  }
  
  /* Секция с видеофоном */
  .hero {
    position: relative;
    height: 90vh;
    width: 100%;
    overflow: hidden;
  }
  
  .video-background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 0;
  }
  
  /* Контент на видео */
  .overlay {
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translateX(-50%);
    z-index: 2;
    text-align: center;
    color: white;
  }
  
  .overlay-logo {
    max-width: 100px;
    margin-bottom: 10px;
  }
  
  .overlay-title {
    font-size: 36px;
    font-weight: bold;
  }
  
  .overlay-subtitle {
    font-size: 20px;
    margin-top: 8px;
    color: #f0f0f0;
  }
  
  /* Контент под видео */
  .hero-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 40px;
    padding: 40px 60px;
    background: #fff4e6;
    flex-wrap: wrap;
  }
  
  .hero-text {
    max-width: 600px;
  }
  
  .hero-text h1 {
    font-size: 36px;
    color: #b5884b;
    margin-bottom: 20px;
  }
  
  .hero-text p {
    font-size: 18px;
    color: #444;
    margin-bottom: 20px;
  }
  
  .hero-text button {
    background-color: #b5884b;
    color: white;
    padding: 12px 24px;
    font-size: 16px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
  }
  
  .hero-text button:hover {
    background-color: #a0743d;
  }
  
  /* Картинка */
  .hero-image {
    max-width: 400px;
    width: 100%;
    border-radius: 12px;
  }
  
  /* Преимущества */
  .features {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    margin-top: 40px;
    gap: 20px;
    padding: 20px;
  }
  
  .feature {
    flex: 1 1 30%;
    background: #fff;
    padding: 20px;
    border-radius: 8px;
    text-align: center;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
  }
  
  .feature h2 {
    color: #b5884b;
    margin-bottom: 10px;
  }
  
  .feature-image {
    margin-top: 15px;
    max-width: 100%;
    height: auto;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  }
  
/* Прочие стили остаются прежними */
</style>