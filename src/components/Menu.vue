<template>
  <div class="menu-container">
    <div class="search-bar">
      <input v-model="searchQuery" placeholder="Поиск..." />
    </div>

    <div class="categories">
      <button
        v-for="category in categories"
        :key="category"
        :class="{ active: selectedCategory === category }"
        @click="selectCategory(category)"
      >
        {{ category }}
      </button>
    </div>

    <div class="products">
      <div
        class="product-card"
        v-for="product in filteredProducts"
        :key="product.id"
      >
        <img :src="product.image" :alt="product.name" />
        <h3>{{ product.name }}</h3>
        <p>{{ product.description }}</p>
        <div class="price">{{ product.price }} ₽</div>
        <button @click="addToCart(product)">Добавить в корзину</button>
      </div>
    </div>

    <div v-if="filteredProducts.length === 0" class="no-results">
      Нет товаров по запросу "{{ searchQuery }}".
    </div>
  </div>
</template>
  
<script>
export default {
  name: "Menu",
  data() {
    return {
      searchQuery: "",
      selectedCategory: "Все",
      categories: [
        "Все",
        "Торты",
        "Кексы",
        "Свежая выпечка",
        "Сэндвичи",
        "Шоколад и конфеты",
        "Печенье",
        "Чай и кофе",
        "Хлеб",
        "Напитки",
        "Фирменные сувениры",
      ],
      products: [
        {
          id: 1,
          category: "Торты",
          name: "Шоколадный торт",
          description: "Насыщенный шоколадный бисквит с кремом ганаш.",
          price: 1200,
          image: "./src/assets/shokolad_tort.png",
        },
        {
          id: 2,
          category: "Торты",
          name: "Медовик",
          description: "Классический торт с мёдом и сметанным кремом.",
          price: 950,
          image: "./src/assets/medovik.png",
        },
          // Кексы
          {
            id: 3,
            category: "Кексы",
            name: "Классический ванильный кекс",
            description: "Лёгкий кекс с натуральной ванилью.",
            price: 150,
            image: "./src/assets/vanilla_cupcake.png",
          },
          {
            id: 4,
            category: "Кексы",
            name: "Шоколадный кекс",
            description: "Нежный шоколадный кекс с кусочками какао.",
            price: 160,
            image: "./src/assets/chocolate_cupcake.png",
          },
          {
            id: 5,
            category: "Кексы",
            name: "Кекс с черникой",
            description: "Ароматный кекс с черникой и ванильной глазурью.",
            price: 170,
            image: "./src/assets/blueberry_cupcake.png",
          },
          {
            id: 6,
            category: "Кексы",
            name: "Кекс с карамелью",
            description: "Сливочный кекс с жидкой карамельной начинкой.",
            price: 180,
            image: "./src/assets/caramel_cupcake.png",
          },
          {
            id: 7,
            category: "Кексы",
            name: "Ореховый кекс",
            description: "Кекс с грецкими орехами и кленовым сиропом.",
            price: 190,
            image: "./src/assets/nut_cupcake.png",
          },
          // Свежая выпечка
          {
            id: 8,
            category: "Свежая выпечка",
            name: "Круассан",
            description: "Слоеный французский круассан с маслом.",
            price: 120,
            image: "./src/assets/croissant.png",
          },
          {
            id: 9,
            category: "Свежая выпечка",
            name: "Булочка с корицей",
            description: "Ароматная булочка с корицей и сахарной глазурью.",
            price: 130,
            image: "./src/assets/cinnamon_roll.png",
          },
          // Сэндвичи
          {
            id: 10,
            category: "Сэндвичи",
            name: "Сэндвич с ветчиной и сыром",
            description: "Хрустящий хлеб с ветчиной, сыром и соусом.",
            price: 250,
            image: "./src/assets/ham_cheese_sandwich.png",
          },
          {
            id: 11,
            category: "Сэндвичи",
            name: "Сэндвич с курицей",
            description: "Нежная куриная грудка, салат и соус в булочке.",
            price: 270,
            image: "./src/assets/chicken_sandwich.png",
          },
          // Шоколад и конфеты
          {
            id: 12,
            category: "Шоколад и конфеты",
            name: "Молочный шоколад",
            description: "Классический молочный шоколад ручной работы.",
            price: 220,
            image: "./src/assets/milk_chocolate.png",
          },
          {
            id: 13,
            category: "Шоколад и конфеты",
            name: "Горький шоколад",
            description: "Шоколад с 70% какао без сахара.",
            price: 230,
            image: "./src/assets/dark_chocolate.png",
          },
          {
            id: 14,
            category: "Шоколад и конфеты",
            name: "Конфета с фундуком",
            description: "Шоколадная конфета с цельным орехом внутри.",
            price: 80,
            image: "./src/assets/hazelnut_candy.png",
          },
          {
            id: 15,
            category: "Шоколад и конфеты",
            name: "Трюфель",
            description: "Мягкий трюфель с какао-порошком.",
            price: 90,
            image: "./src/assets/truffle.png",
          },
          // Печенье
          {
            id: 16,
            category: "Печенье",
            name: "Овсяное печенье",
            description: "Мягкое печенье с овсянкой и мёдом.",
            price: 180,
            image: "./src/assets/oatmeal_cookie.png",
          },
          {
            id: 17,
            category: "Печенье",
            name: "Шоколадное печенье",
            description: "Печенье с кусочками черного шоколада.",
            price: 190,
            image: "./src/assets/chocolate_cookie.png",
          },
          // Чай и кофе
          {
            id: 18,
            category: "Чай и кофе",
            name: "Чёрный чай",
            description: "Ароматный крупнолистовой чёрный чай.",
            price: 100,
            image: "./src/assets/black_tea.png",
          },
          {
            id: 19,
            category: "Чай и кофе",
            name: "Зелёный чай",
            description: "Лёгкий и свежий зелёный чай.",
            price: 110,
            image: "./src/assets/green_tea.png",
          },
          {
            id: 20,
            category: "Чай и кофе",
            name: "Американо",
            description: "Классический чёрный кофе.",
            price: 150,
            image: "../src/assets/americano.png",
          },
          {
            id: 21,
            category: "Чай и кофе",
            name: "Капучино",
            description: "Кофе с молочной пенкой.",
            price: 170,
            image: "./src/assets/cappuccino.png",
          },
          // Хлеб
          {
            id: 22,
            category: "Хлеб",
            name: "Пшеничный хлеб",
            description: "Свежий пшеничный хлеб с хрустящей корочкой.",
            price: 60,
            image: "./src/assets/white_bread.png",
          },
          {
            id: 23,
            category: "Хлеб",
            name: "Ржаной хлеб",
            description: "Ароматный ржаной хлеб с семенами.",
            price: 70,
            image: "./src/assets/rye_bread.png",
          },
          // Напитки
          {
            id: 24,
            category: "Напитки",
            name: "Морс клюквенный",
            description: "Освежающий домашний морс.",
            price: 130,
            image: "./src/assets/mors.png",
          },
          {
            id: 25,
            category: "Напитки",
            name: "Апельсиновый лимонад",
            description: "Газированный напиток с апельсином.",
            price: 140,
            image: "./src/assets/lemonade.png",
          },
          // Сувениры
          {
            id: 26,
            category: "Фирменные сувениры",
            name: "Фирменная кружка",
            description: "Керамическая кружка с логотипом.",
            price: 350,
            image: "./src/assets/mug.png",
          },
          {
            id: 27,
            category: "Фирменные сувениры",
            name: "Эко-сумка",
            description: "Удобная сумка с фирменным дизайном.",
            price: 400,
            image: "./src/assets/eco_bag.png",
          },
        ],
      };
    },
computed: {
    filteredProducts() {
      return this.products.filter(
        (product) =>
          (this.selectedCategory === "Все" || product.category === this.selectedCategory) &&
          product.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
  methods: {
    selectCategory(category) {
      this.selectedCategory = category;
    },
    addToCart(product) {
      this.$emit("add-to-cart", product); // ← отправка товара в App.vue
    },
  },
};
  </script>
  
  <style scoped>
  .menu-container {
    padding: 20px;
    max-width: 1200px;
    margin: auto;
  }
  .search-bar input {
    width: 100%;
    padding: 10px;
    margin-bottom: 20px;
    font-size: 16px;
  }
  .categories {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 20px;
  }
  .categories button {
    padding: 10px 20px;
    border: none;
    cursor: pointer;
    background: #ffffff;
    border-radius: 4px;
    font-weight: bold;
  }
  .categories button.active {
    background: #d48b43;
    color: white;
  }
  .products {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px;
  }
  .product-card {
    background: white;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 15px;
    text-align: center;
  }
  .product-card img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    border-radius: 4px;
  }
  .product-card h3 {
    margin: 10px 0 5px;
  }
  .product-card p {
    margin: 5px 0;
  }
  .product-card .price {
    font-weight: bold;
    margin: 10px 0;
  }
  .product-card button {
  background-color: #ff7f50;
  color: white;
  border: none;
  padding: 10px;
  margin-top: 10px;
  cursor: pointer;
  border-radius: 8px;
  transition: 0.3s ease;
}
.product-card button:hover {
  background-color: #ff5722;
}
  .no-results {
    text-align: center;
    font-size: 18px;
    color: #666;
  }
  </style>
  