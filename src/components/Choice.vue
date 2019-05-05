<template>
  <form>
    <p>Choice label: 
      <select v-model="choiceLabel">
        <option v-for="label in labelArray">{{ label.name }}</option>
      </select>
    </p>
    <p>Choice text: 
      <input type="text" v-model="choice">
    </p>
    <input type="submit" value="Add Choice">
  </form>
</template>

<script>
export default {
  name: 'Menu',
  props: {
    choiceLabel: String,
    labelArray: Array,
    choice: String
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