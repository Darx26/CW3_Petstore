<template>
  <div id="app">
    <header>
      <h1>{{ sitename }}</h1>
      <button @click="showCheckout">{{ this.cart.length }}Checkout</button>
    </header>
    <main>
      <product-list @addProduct="addToCart" v-if="showLesson"></product-list>
      <checkout :cart="cart" @remove-item="removeFromCart" v-else></checkout>
    </main>
  </div>
</template>

<script>
import productList from './components/ProductList.vue';
import checkout from './components/Form.vue';
export default{
  components: { 
    productList, checkout
  },
  name: "App",
  data(){
    return{
      sitename: "Vue.js Pet Depot",
      cart: [],
      showLesson: true
    }
  },
  methods: {
    showCheckout(){
      this.showLesson = this.showLesson ? false : true;
    },
    addToCart(product){
      console.log("addProduct event received by the root component.");
      this.cart.push(product);
    },
    removeFromCart(index){
      console.log("remove-item event received by the root component.");
      this.cart.splice(index, 1);
    }
  },
};
</script>
