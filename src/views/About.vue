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
      // message: "# Characters used in-game\ndefine s = Character(_(\"Sylvie\"), color=\"#333333\")\nlabel meadow\nscene bg school\nwith fade\n\tshow sylvie green smile\n\ts Hi, I'm Sylvie!\n\tmenu lunch\n\t\tWhere should we eat?\n\t\tGrab a burger\n\t\t\tjump burger\n\t\tGet tacos\n\t\t\tjump tacos\n",
      labels: [],
      characters: [],
      methods: {
        
      }
    };
  },
  created: function() {
    axios.get("/api/labels/final").then(response => {
      this.output = response.data;
    })
  }
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