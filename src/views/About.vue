<template>
  <div class="about">
    <h1>Final RenPy Code</h1>
     <textarea name="final" rows="20" cols="30">
        {{ message }}
      </textarea>
  </div>
</template>

<script>
  import axios from "axios";
  export default {
  data: function() {
    return {
      message: "Hello to Vue.js!",
      labels: [],
    };
  },
  // return_final: function() {
  //   axios.get("/api/labels/final").then(response => {
  //     this.labels = response.data;
  //   })
  // },
  // methods: {
  //   addNewFinal: function() {
  //     console.log('printing final...');
  //     var params = {
  //       input_name: this.newProductName,
  //       input_price: this.newProductPrice,
  //       input_description: this.newProductDescription
  //     }
  //   }
  // }
};
</script>