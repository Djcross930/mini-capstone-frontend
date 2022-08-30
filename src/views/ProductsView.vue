<script>
import axios from 'axios'
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      products: []
    };
  },
  created: function () {
    this.indexProducts()
  },
  methods: {
    indexProducts: function () {
      axios.get("/products").then((response) => {
        console.log("products index", response);
        this.products = response.data;
      });
    }
  },
};
</script>
  
  <template>
  <div class="home">
    <div v-for="product in products">
      <a v-bind:href="`/products/${product.id}`"> {{  product.name  }} Go somewhere</a>
      <p> {{  product.price  }} </p>
      <br />
    </div>
  </div>
</template>
  
  <style>
  </style>