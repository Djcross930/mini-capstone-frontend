<script>
import axios from "axios";
export default {
  data: function () {
    return {
      product: {},
      editproductParams: {},
      errors: [],
    };
  },
  created: function () {
    axios.get("/products/" + this.$route.params.id).then((response) => {
      console.log("products show", response.data);
      this.product = response.data;
    });
  },
  methods: {
    updateProduct: function () {
      axios.patch("/products/" + this.$route.params.id + ".json", this.product)
      console.log(response.data)
    }
  },
};
</script>
  
  <template>
  <div class="products-edit">
    <h1>{{  product.name  }}</h1>
    <h1>{{  product.price  }}</h1>
    <h1>{{  product.description  }}</h1>
    <p>name: <input type="text" v-model="product.name" /></p>
    <div>price: <input type="text" v-model="product.price" /></div>
    <p>description: <input type="text" v-model="product.description" /></p>
    <button v-on:click="updateProduct()">Update</button>

    <button v-on:click="deleteProduct()">Delete Product</button>
  </div>
</template>