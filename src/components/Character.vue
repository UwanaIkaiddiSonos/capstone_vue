<template>
  <form>
    <p>Character: 
      <select v-model="firstName">
        <option v-for="character in characters">{{ character.first_name }}</option>
      </select>
    </p>
    <!-- <p>Character: <select v-model="newCharacter.firstName" v-on:change="setColor($event)">
      <option v-for="character in characters">{{ character.first_name }}</option>
    </select><br> -->
    <!--Need to figure out how to connect character name and color-->
    <!-- <p>Color: <input type="color" name="color" v-for="character.color"></p> -->

    <p>Dialogue: 
      <textarea name="dialogue" v-model="dialogueText" rows="2" cols="30"> 
        Enter your character's dialogue...
      </textarea>
    </p>
    <input type="submit" value="Add more dialogue">
  </form>
</template>

<script>
export default {
  name: 'Character',
  props: {
    firstName: String,
    characters: Array,
    dialogueText: String
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