<template>
  <div class="about">
    <h1>Final RenPy Code</h1>
     <textarea readonly name="final" rows="20" cols="30">{{ output['output'] }}
      </textarea>
  </div>
</template>

<script>
  import axios from "axios";
  export default {
  data: function() {
    return {
      output: "",
      labels: [],
      characters: [],
      methods: {
      }
    };
  },
  created: function() {
    axios.get("/api/drafts").then(response => {
      this.output = response.data;
    })
  }
};
</script>