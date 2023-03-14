<template>
  <body>
    
    <div class="products">
      <div class="product-card" v-for="product in products" :key="product.id">
        <div class="product-image">
          <img :src="product.imgURL" :alt="product.prodDescription" />
        </div>
        <div class="product-details">
          <h2>{{ product.prodName }}</h2>
          <h3>{{ product.prodDescription }}</h3>
          <p>R{{ product.price }}</p>
        </div>
        <div class="product-actions">
          <button @click="addToCart(product)">Add to Cart</button>
          <button @click="viewMore(product)">View More</button>
        </div>
      </div>
    </div>
  </body>
</template>

<script>
import { useStore } from "vuex";
import { computed } from "@vue/runtime-core";

export default {
  setup() {
    const store = useStore();
    store.dispatch("fetchProducts");
    const products = computed(() => store.state.products);

    function addToCart(product) {
      store.dispatch("addToCart", product);
    }

    function viewMore(product) {
      console.log(`View more details for product ${product.id}`);
    }

    return {
      products,
      addToCart,
      viewMore,
    };
  },
};
</script>

  
  <style scoped>

  body {
    position: relative;
    background-image: url('https://i.postimg.cc/4ymwDgqT/Archie-Vable-Gaming-Logo.png');
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    font-family: Arial, sans-serif;
    margin: 0;
    z-index: 1;
  }
  button {
    background-color: grey;
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
    border-radius: 5px;
  }

  button:hover{
    background-color: green;
  }
  
  
  .products {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    z-index: 10000000000000000000;
  }

  .products {
    padding-top: 60px;
  }
  @media (max-width: 979px) {
    .products {
      padding-top: 50px;
    }
  }
  
  .product-card {
    margin: 10px;
    border-radius: 5px;
    background-color: white;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.3);
    transition: all 0.3s ease-in-out;
    max-width: 350px;
  }
  
  .product-card:hover {
    transform: translateY(-5px);
  }
  
  .product-image {
    width: 100%;
    height: 250px;
    overflow: hidden;
    border-radius: 5px 5px 0 0;
  }
  
  .product-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .product-details {
    padding: 20px;
    text-align: center;
  }
  
h3{
  color: grey;
}

  .product-details h2 {
    margin: 0;
    font-size: 1.5rem;
  }
  
  .product-details p {
    margin-top: 10px;
    font-size: 1.2rem;
    font-weight: bold;
  }
  </style>