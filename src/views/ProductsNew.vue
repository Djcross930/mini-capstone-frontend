<script>
import axios from "axios";
export default {
  data: function () {
    return {
      newProductParams: {},
      errors: [],
    };
  },
  methods: {
    submit: function () {
      axios
        .post("/products.json", this.newProductParams)
        .then((response) => {
          console.log(response.data);
          this.$router.push("/products");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>
<template>
  <div class="products-new">
    <form v-on:submit.prevent="submit()">
      <h1>Make a new Product</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{  error  }}</li>
      </ul>
      <div>
        <label>Name:</label>
        <input type="text" v-model="newProductParams.name" />
      </div>
      <div>
        <label>Price:</label>
        <input type="text" v-model="newProductParams.price" />
      </div>
      <div>
        <label>Description:</label>
        <input type="text" v-model="newProductParams.description" />
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>