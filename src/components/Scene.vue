<template>
  <form>
    <p>Scene: 
      <select v-model="sceneName">
        <option v-for="background_image in bgArray">{{ background_image.scene_name }}</option>
      </select>
    </p>

    <p>Transition:  
      <select v-model="transitionName">
        <option v-for="transition in transArray">{{ transition.name }}</option>
      </select>
    </p>
  </form>
</template>

<script>
export default {
  name: 'Scene',
  props: {
    sceneName: String,
    bgArray: Array,
    transitionName: String,
    transArray: Array
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