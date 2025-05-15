<template>
  <div class="background-wrapper">
    <div>
      <header class="navbar">
        <img src="./assets/logo.png.png" alt="British Bakery" class="logo" />

        <nav>
          <button @click="currentView = 'Home'">Главная</button>
          <button @click="currentView = 'Menu'">Меню</button>
          <button @click="currentView = 'About'">О нас</button>
          <button @click="currentView = 'Bakeries'">Пекарни</button>
          <button @click="currentView = 'Contact'">Контакты</button>
        </nav>

        <div class="header-right">
          <!-- Корзина -->
          <div class="cart" @click="openCartModal">
            <img src="./assets/cart-icon.png" alt="Корзина" class="cart-icon" />
            <span v-if="cartItems.length === 0"></span>
            <span v-else>{{ cartItems.length }} позиций</span>
          </div>

          <!-- Профиль -->
          <div class="profile">
            <template v-if="user">
              <span class="username">Привет, {{ user.name }}</span>
              <button @click="logout" class="logout-button">Выйти</button>
            </template>
            <template v-else>
              <img src="./assets/user-icon.png" alt="Профиль" class="profile-icon" @click="openProfileModal" />
            </template>
          </div>
        </div>
      </header>

<!-- Модальное окно корзины -->
<div v-if="isCartModalVisible" class="cart-modal">
  <div class="cart-modal-content">
    <h2>Ваша корзина</h2>
    <div v-if="cartItems.length === 0">
      <p>Корзина пуста. Добавьте товары.</p>
    </div>
    <div v-else>
      <ul>
        <li v-for="(item, index) in cartItems" :key="index">
          {{ item.name }} - {{ item.price }}₽
          <button @click="removeFromCart(index)">Удалить</button>
        </li>
      </ul>
      <p><strong>Итого: {{ totalPrice }}₽</strong></p>
      <button @click="openCheckout">Оформить заказ</button>
    </div>
    <button @click="closeCartModal" class="cancel">Закрыть</button>
  </div>
</div>

<!-- Модальное окно оформления заказа -->
<div v-if="showCheckout" class="cart-modal">
  <div class="cart-modal-content">
    <h2>Оформление заказа</h2>
    <input v-model="address" placeholder="Введите ваш адрес" />
    <label>
      <input type="radio" value="cash" v-model="paymentMethod" /> Оплата наличными
    </label>
    <!-- Можно позже добавить и другие методы -->
    <button @click="placeOrder">Подтвердить заказ</button>
    <button @click="closeCheckout" class="cancel">Отмена</button>
  </div>
</div>


      <!-- Модальное окно профиля -->
      <div v-if="isProfileModalVisible" class="cart-modal">
        <div class="cart-modal-content">
          <h2>Регистрация</h2>
          <input v-model="name" placeholder="Имя" />
          <input v-model="email" type="email" placeholder="Email" />
          <input v-model="password" type="password" placeholder="Пароль" />
          <button @click="register">Зарегистрироваться</button>
          <button @click="closeProfileModal" class="cancel">Отмена</button>
        </div>
      </div>

      <main>
        <component
  :is="currentViewComponent"
  @navigate="currentView = $event"
  @add-to-cart="handleAddToCart"
/>
      </main>

      <!-- Футер -->
      <footer class="footer">
        <div class="footer-left">
          <ul>
            <li><a href="#" @click.prevent="currentView = 'Home'">Главная</a></li>
            <li><a href="#" @click.prevent="currentView = 'Menu'">Меню</a></li>
            <li><a href="#" @click.prevent="currentView = 'About'">О нас</a></li>
            <li><a href="#" @click.prevent="currentView = 'Bakeries'">Пекарни</a></li>
            <li><a href="#" @click.prevent="currentView = 'Contact'">Контакты</a></li>
          </ul>
        </div>

        <div class="footer-center">
          <h3>Контакты</h3>
          <p>Телефон: 611-24-00</p>
          <p>e-mail для физ.лиц: <a href="mailto:mail@peterbakery.ru">mail@peterbakery.ru</a></p>
          <p>e-mail для юр.лиц: <a href="mailto:4205621@mail.ru">4205621@mail.ru</a></p>
          <p>e-mail для арендодателей: <a href="mailto:al-109@mail.ru">al-109@mail.ru</a></p>
          <p>отдел франчайзинга: <a href="mailto:partner@peterbakery.ru">partner@peterbakery.ru</a></p>
        </div>

        <div class="footer-right">
          <div class="social-icons">
            <a href="https://vk.com/feed" target="_blank" class="footer-social-link">
              <img src="./assets/logo1.png" alt="ВКонтакте" class="footer-logo" />
            </a>
            <a href="https://web.telegram.org" target="_blank" class="footer-social-link">
              <img src="./assets/logo2.png" alt="Telegram" class="footer-logo" />
            </a>
            <a href="https://www.pochta.ru" target="_blank" class="footer-social-link">
              <img src="./assets/logo3.png" alt="Почта" class="footer-logo" />
            </a>
          </div>
        </div>
      </footer>
    </div>
  </div>
</template>

<script>
import Home from './components/Home.vue'
import Menu from './components/Menu.vue'
import About from './components/About.vue'
import Bakeries from './components/Bakeries.vue'
import Contact from './components/Contact.vue'

export default {
  components: { Home, Menu, About, Bakeries, Contact },
  data() {
    return {
      currentView: 'Home',
      cartItems: [],
      isCartModalVisible: false,
      isProfileModalVisible: false,
      showCheckout: false,
      name: '',
      email: '',
      password: '',
      address: '',
      paymentMethod: 'cash',
      user: null
    }
  },

  computed: {
    currentViewComponent() {
      return this.currentView
    },
    totalPrice() {
      return this.cartItems.reduce((sum, item) => sum + item.price, 0)
    }
  },

  methods: {
    // Переключатели модалок
    openCartModal() {
      this.isCartModalVisible = true
    },
    closeCartModal() {
      this.isCartModalVisible = false
    },
    openProfileModal() {
      this.isProfileModalVisible = true
    },
    closeProfileModal() {
      this.isProfileModalVisible = false
    },
    openCheckout() {
      this.showCheckout = true
    },
    closeCheckout() {
      this.showCheckout = false
    },

    // Работа с корзиной
    handleAddToCart(product) {
      this.cartItems.push(product)
    },
    removeFromCart(index) {
      this.cartItems.splice(index, 1)
    },

    // Оформление заказа
    placeOrder() {
      if (!this.address) {
        alert('Пожалуйста, введите адрес.')
        return
      }

      let userEmail = this.user?.email || 'Гость'
      alert(`Спасибо за заказ!\n\nАдрес: ${this.address}\nОплата: ${this.paymentMethod === 'cash' ? 'Наличными' : 'Другое'}\nEmail: ${userEmail}`)

      // Очистка состояния
      this.cartItems = []
      this.address = ''
      this.paymentMethod = 'cash'
      this.showCheckout = false
      this.isCartModalVisible = false
    },

    // Регистрация
    register() {
      if (this.name && this.email && this.password) {
        this.user = {
          name: this.name,
          email: this.email
        }

        // Очистка формы
        this.name = ''
        this.email = ''
        this.password = ''
        this.isProfileModalVisible = false
      } else {
        alert('Пожалуйста, заполните все поля.')
      }
    },

    // Выход из профиля
    logout() {
      this.user = null
    }
  }
}
</script>

<style scoped>
.background-wrapper {
  min-height: 100vh;
  background-image: url('./assets/background.jpg'); /* путь к твоему изображению */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
  display: flex;
  flex-direction: column;
}

/* Убедись, что body и html не ограничивают размер */
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
}
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #ffffff;
  padding: 10px 40px;
  border-bottom: 1px solid #ffffff;
  position: relative;
}

.logo {
  height: 40px;
}

nav {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 20px;
}

nav button {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 16px;
  color: #333;
}

nav button:hover {
  color: #b5884b;
}

/* Стили для корзины */
.cart {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 14px;
  color: #333;
  cursor: pointer;
}

.cart-icon {
  height: 30px;
}

.cart span {
  font-weight: 600;
}
/* Стили для модального окна */
.cart-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.cart-modal-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  text-align: center;
  width: 300px;
}

.cart-modal-content button {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #b5884b;
  border: none;
  color: white;
  cursor: pointer;
}

.cart-modal-content button:hover {
  background-color: #a07743;
}
.header-right {
  display: flex;
  align-items: center;
  gap: 20px;
}

.profile-icon {
  height: 30px;
  cursor: pointer;
}

.username {
  font-weight: 600;
  color: #333;
}

.logout-button {
  margin-left: 10px;
  padding: 5px 10px;
  background-color: #e74c3c;
  border: none;
  color: white;
  cursor: pointer;
  border-radius: 5px;
}

.logout-button:hover {
  background-color: #c0392b;
}

input {
  display: block;
  width: 100%;
  margin: 10px 0;
  padding: 8px;
  font-size: 14px;
}

.cancel {
  margin-top: 10px;
  background: gray;
}
/* Footer styles */
.footer {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  background-color: #f6f6f6;
  padding: 30px 60px;
  flex-wrap: wrap;
  margin-top: 60px;
  border-top: 1px solid #ddd;
}

.footer-left, .footer-center, .footer-right {
  flex: 1 1 30%;
  padding: 10px;
}

.footer-left ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-left li {
  margin-bottom: 10px;
}

.footer-left a {
  text-decoration: none;
  color: #333;
  font-weight: 500;
  transition: color 0.3s ease;
}

.footer-left a:hover {
  color: #b5884b;
}

.footer-center {
  font-size: 14px;
  color: #444;
}

.footer-center h3 {
  color: #b5884b;
  margin-bottom: 10px;
}

.footer-center p {
  margin: 5px 0;
}

.footer-center a {
  color: #b5884b;
  text-decoration: none;
}

.footer-center a:hover {
  text-decoration: underline;
}

.footer-right {
  display: flex;
  flex-direction: column;
  gap: 15px;
  align-items: center;
}

.footer-social-link {
  display: inline-block;
  margin: 0 10px;
}

.footer-logo {
  width: 50px;
  height: 270px;
  object-fit: contain;
  transition: transform 0.3s ease;
}

.footer-logo:hover {
  transform: scale(1.1);
}

</style>