<template>
  <div class="new">
    <h1> {{ message }} </h1>
    <p>Text</p>
  </div>
</template>

<script>
  import axios from "axios";
  export default {
  data: function() {
    return {
      message: "This is the NEW page",
  //     methods: {
  //     }
  //   };
  // },
  // created: function() {
  //   axios.get("/api/drafts").then(response => {
  //     this.output = response.data;
  //   })
  }
  };
</script>