<template>
  <div class="container">
    <!-- Вакансии -->
    <section class="section">
      <h2>Открытие новых Британсих пекарен!</h2>
      <p class="subtitle">Скоро открытие: ул. Володарского, 2 (Левашово)</p>
      <p class="subtitle">Приглашаем на работу:</p>
      <ul>
        <li>— Продавец-кассир</li>
        <li>— Повар-универсал</li>
        <li>— Уборщица / мойщик посуды</li>
      </ul>
      <p>Звоните по вопросам трудоустройства: <strong>+7 (911) 170-13-16 (Ренат)</strong></p>
    </section>

    <!-- Продавец-кассир -->
    <section class="job-card">
      <h3>Продавец-кассир</h3>
      <p>Работа с гостями, продажа выпечки, поддержание чистоты и уюта.</p>
      <p><strong>Условия:</strong></p>
      <ul>
        <li>— Оплата от 3000₽ за смену + премии</li>
        <li>— Гибкий график</li>
        <li>— Бесплатное питание</li>
        <li>— Оформление по ТК РФ</li>
      </ul>
      <p><strong>Адреса:</strong></p>
      <ul>
        <li>— пр. Ленинский, 54</li>
        <li>— пр. Европейский, 22 (Кудрово)</li>
        <li>— пр. Комендантский, 66к3</li>
        <li>— ул. Маршала Казакова, 21к3</li>
      </ul>
    </section>

    <!-- Повар-универсал -->
    <section class="job-card">
      <h3>Повар-универсал</h3>
      <p>Приготовление блюд, соблюдение санитарных норм, работа по технологическим картам.</p>
      <p><strong>Требования:</strong></p>
      <ul>
        <li>— Опыт или профильное образование</li>
        <li>— Аккуратность и ответственность</li>
        <li>— Медкнижка (желательно)</li>
      </ul>
      <p><strong>Условия:</strong></p>
      <ul>
        <li>— Зарплата от 50 000₽</li>
        <li>— График 2/2 или по договорённости</li>
        <li>— Бесплатное питание, форма</li>
        <li>— Возможность роста</li>
      </ul>
    </section>

    <!-- Контакты -->
    <section class="section">
      <h2>Контакты</h2>
      <ul>
        <li><strong>Телефон:</strong> +7 (812) 614-65-61</li>
        <li><strong>Офис:</strong> info@baltic-bread.ru</li>
        <li><strong>Опт:</strong> opt@baltic-bread.ru</li>
        <li><strong>Интернет-магазин:</strong> help@british-bakery.ru</li>
        <li><strong>Кадры:</strong> personal@baltic-bread.ru</li>
        <li><strong>Маркетинг:</strong> marketing@baltic-bread.ru</li>
      </ul>
    </section>

    <!-- Форма обратной связи -->
    <section class="form-section">
      <h2>Напишите нам</h2>
      <form @submit.prevent="submitForm">
        <div>
          <input v-model="form.name" type="text" placeholder="Ваше имя" />
          <p v-if="errors.name" class="error">{{ errors.name }}</p>
        </div>

        <div>
          <input v-model="form.email" type="email" placeholder="Email" />
          <p v-if="errors.email" class="error">{{ errors.email }}</p>
        </div>

        <div>
          <input v-model="form.phone" type="tel" placeholder="Телефон" />
          <p v-if="errors.phone" class="error">{{ errors.phone }}</p>
        </div>

        <div>
          <textarea v-model="form.message" placeholder="Ваше сообщение"></textarea>
          <p v-if="errors.message" class="error">{{ errors.message }}</p>
        </div>

        <button type="submit">Отправить</button>
      </form>

      <!-- Модальное окно -->
      <div v-if="showModal" class="modal-overlay" @click.self="showModal = false">
        <div class="modal">
          <p>Спасибо! Мы свяжемся с вами.</p>
          <button @click="showModal = false">Ок</button>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

const form = reactive({
  name: '',
  email: '',
  phone: '',
  message: ''
})

const errors = reactive({
  name: '',
  email: '',
  phone: '',
  message: ''
})

const showModal = ref(false)

function validateForm() {
  let valid = true
  errors.name = form.name ? '' : 'Введите имя'
  errors.email = /^\S+@\S+\.\S+$/.test(form.email) ? '' : 'Некорректный email'
  errors.phone = /^\+?[0-9\s\-()]{7,20}$/.test(form.phone) ? '' : 'Некорректный телефон'
  errors.message = form.message ? '' : 'Введите сообщение'

  for (let key in errors) {
    if (errors[key]) valid = false
  }
  return valid
}

function submitForm() {
  if (!validateForm()) return
  console.log('Форма отправлена:', form)
  showModal.value = true
  form.name = ''
  form.email = ''
  form.phone = ''
  form.message = ''
}
</script>

<style scoped>
.container {
  max-width: 900px;
  margin: auto;
  padding: 24px;
  font-family: 'Arial', sans-serif;
  line-height: 1.6;
  background-color: #ffffffc6;
  border-radius: 8px;
}

.section {
  margin-bottom: 40px;
}

.job-card {
  border: 1px solid #ddd;
  padding: 20px;
  margin-bottom: 30px;
  border-radius: 8px;
  background: #ffffff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h2 {
  font-size: 28px;
  margin-bottom: 12px;
  color: #333;
  text-align: center;
}

h3 {
  font-size: 24px;
  margin-bottom: 10px;
  color: #444;
}

ul {
  padding-left: 20px;
}

li {
  margin-bottom: 8px;
  color: #555;
}

.subtitle {
  font-weight: bold;
  margin-top: 10px;
  font-size: 18px;
  color: #666;
}

.form-section {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.form-section form {
  display: flex;
  flex-direction: column;
  gap: 14px;
  width: 100%;
  max-width: 500px; /* Устанавливаем максимальную ширину формы */
  margin: 0 auto;
}

form input,
form textarea {
  padding: 12px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 6px;
  background-color: #fafafa;
  transition: all 0.3s ease;
  width: 100%; /* Поля занимают всю доступную ширину */
  max-width: 500px; /* Максимальная ширина для полей */
}

form input:focus,
form textarea:focus {
  border-color: #8e44ad;
  background-color: #fff;
}

form textarea {
  resize: vertical;
  min-height: 120px;
}

form button {
  background: #e4884f;
  color: white;
  padding: 12px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s ease;
  width: 100%;
  max-width: 500px; /* Максимальная ширина для кнопки */
}

form button:hover {
  background: #e8620e;
}

.error {
  color: #e74c3c;
  font-size: 14px;
  margin-top: 4px;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.4);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal {
  background: #ffffff;
  padding: 24px 32px;
  border-radius: 8px;
  text-align: center;
  max-width: 320px;
  width: 100%;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.modal p {
  font-size: 18px;
  color: #555;
}

.modal button {
  margin-top: 16px;
  padding: 12px 24px;
  background: #d16a48;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s ease;
}

.modal button:hover {
  background: #ed4b19bc;
}
</style>
