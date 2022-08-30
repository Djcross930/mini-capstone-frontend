<script>
import axios from 'axios';
export default {
  data: function () {
    return {
      product: {},
    };
  },
  created: function () {
    console.log('in show product')
    console.log(this.$route.params.id)
    axios.get("/products/" + this.$route.params.id + ".json").then(response => {
      console.log(response.data);
      this.product = response.data;
    })
  },
  methods: {},
};
</script>
  
  <template>
  <div class="products-show">
    <h1>{{  product.name  }}</h1>
    <p> {{  product.price  }}</p>
    <p> {{  product.description  }} </p>
    <button>Add to Cart</button>
    <br />
    <a v-bind:href="`/products/${product.id}/edit`">Edit</a>
  </div>
</template>