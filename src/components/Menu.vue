<template>
  <form>
    <p>Menu: 
      <select v-model="menuName">
        <option v-for="label in labelArray">{{ label.name }}</option>
      </select>
    </p>
    <p>Intro line: 
      <input type="text" v-model="introText">
    </p>
  </form>
</template>

<script>
export default {
  name: 'Menu',
  props: {
    menuName: String,
    labelArray: Array,
    introText: String
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