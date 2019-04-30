<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <form>
      <p>First Name: <input type="text" v-model="newCharacter.firstName"></p>
      <p>Last Name: <input type="text" v-model="newCharacter.lastName"></p>
      <p>Color: <input type="color" v-model="newCharacter.color"></p>
    <button v-on:click.prevent="addCharacter()">Create character</button>
    </form>
<hr>
    <form> <!--Label form-->
      <p>Scene: <select>
        <option v-for="background_image in background_images">{{ background_image.name }}</option>
      </select></p>

      <p>Transition:  <select name="transition">
        <option v-for="transition in transitions">{{ transition.name }}</option>
      </select></p>
    </form>
<hr>
    <form>
      <p>Character: <select>
        <option v-for="character in characters">{{ character.first_name }}</option>
      </select><br>
      Dialogue: <textarea name="dialogue" rows="2" cols="30">
        Enter your character's dialogue...
      </textarea>
      </p>
      <input type="submit" value="Add more dialogue">
    </form>
<hr>

    <form> <!--Menu form-->
      <p>Intro line: <input type="text" name="intro_line"></p>
      <p>Choice 1 label: <select name="labels">
        <option v-for="label in labels">{{ label.name }}</option>
      </select></p>
      <p>Choice 1 text: <input type="text" name="choice1"></p>
      <p>Choice 2 label: <select name="labels">
        <option v-for="label in labels">{{ label.name }}</option>
      </select></p>
      <p>Choice 2 text: <input type="text" name="choice1"></p>
      <input type="submit" value="Add Choice">
    </form>
<hr>
    <form>
      <input type="submit" value="Add label">
    </form>
  </div>
</template>

<script>
import axios from "axios";
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  data: function() {
    return {
      message: "Hello world!",
      characters: [],
      newCharacter: {
        firstName: "",
        lastName: "",
        color: "#000000"
      },
      background_images: [],
      newScene: {
        name: ""
      },
      labels: [],
      newLabel: {
        name: ""
      },
      transitions: [],
      newTransition: {
        name: ""
      },
    };
  },
  created: function() {
    axios.get("/api/characters").then(response => {
      this.characters = response.data;
    });
    axios.get("/api/background_images").then(response => {
      this.background_images = response.data;    
    });
    axios.get("/api/transitions").then(response => {
      this.transitions = response.data;    
    });
    axios.get("/api/labels").then(response => {
      this.labels = response.data;    
    })
  },
  methods: {
    addCharacter: function() {
      console.log('editing contact');
      var params = {
        input_first_name: this.newCharacter.firstName,
        input_last_name: this.newCharacter.lastName,
        input_color: this.newCharacter.color
      }
      axios.post("/api/characters", params).then(response => {
        console.log(response);
      });
    }
  }
};
</script>
