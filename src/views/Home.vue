<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <form>
      <p>Label:  <select v-model="newLabel.name" name="labels">
        <option v-for="label in labels">{{ label.name }}</option>
       </select></p>
    </form>
<hr>
    <form> <!--Label form-->
      <p>Scene: <select v-model="newScene.name" name="scenes">
        <option v-for="background_image in background_images">{{ background_image.scene_name }}</option>
      </select></p>

      <p>Transition:  <select v-model="newTransition.name" name="transition">
        <option v-for="transition in transitions">{{ transition.name }}</option>
      </select></p>
    </form>
<hr>
    <form>
      <p>Character: <select v-model="newCharacter.firstName">
        <option v-for="character in characters">{{ character.first_name }}</option>
      </select><br>
      <!--Need to figure out how to connect character name and color-->
      <select v-model="newCharacter.color">
        <option v-for="character in characters">{{ character.color }}</option>
      </select><br>
      Dialogue: <textarea v-model="dialogue" name="dialogue" rows="2" cols="30">
        Enter your character's dialogue...
      </textarea>
      </p>
      <input type="submit" value="Add more dialogue">
    </form>
<hr>

    <form> <!--Menu form-->
      <p>Menu: <select name="labels">
        <option v-for="label in labels">{{ newLabel.labelName }}</option>
       </select></p>
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
    <form v-on:submit.prevent="Generate()">
      <input type="submit" value="Generate"><br><br>
      <textarea readonly name="final" rows="20" cols="30">{{ output['output'] }}
      </textarea>
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
      output: "",
      message: "Hello world!",
      characters: [],
      newCharacter: {
        firstName: "",
        lastName: "",
        color: ""
      },
      background_images: [],
      newScene: {
        sceneName: ""
      },
      labels: [],
      newLabel: {
        labelName: ""
      },
      transitions: [],
      newTransition: {
        transitionName: ""
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
    Generate: function() {
      console.log('translating into RenPy syntax');
      var params = {
        input_first_name: this.newCharacter.firstName,
        input_color: this.newCharacter.color,
        input_label_name: this.newLabel.name,
        input_scene_name: this.newScene.sceneName,
        input_transition_name: this.newTransition.transitionName
      }
      console.log(params)
      axios.post("/api/drafts", params).then(response => {
      this.output = response.data;
      });
    }
  }
};
</script>
