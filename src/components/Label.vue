<template>
  <form>
    <p>Label:  
      <select v-model="labelN">
        <option v-for="label in labelArray">{{ label.name }}</option>
      </select>
    </p>
  </form>
</template>

<script>

export default {
  name: 'Label',
  props: {
    labelName: String,
    labelArray: Array
  },
  data: function() {
    return {
      labelN: this.labelName,
      labelA: this.labelArray,
      methods: {
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>