<template>
  <div class="wrapper">
  <!--Left segment-->
  <section class="split-image parallax" data-background="assets/images/module-7.jpg">
    <div class="container-fluid container-custom">
      <br><br>
              <textarea readonly name="final" rows="30" cols="30">{{ output['output'] }}
              </textarea>
    </div>
  </section>
  <!--Left segment end-->
  <!--Right segment-->
  <section class="split-content">
    <!--Insert content here-->
    <section class="module">
      <div class="container-fluid container-custom">
          <div class="home">
          <h1>{{ message }}</h1>

          <!-- Label Section -->

          <!-- <Label labelName="newLabel.labelName" v-bind:labelArray="labels"></Label> -->
          <button v-on:click="addLabel()">Add new label dropdown</button>
          <form>
            <div v-for="oneLabel, $index in listOfLabels">
            <p>Label:  
              <select v-model="selectedLabels[$index]">
                <option v-for="label in oneLabel">{{ label.name }}</option>
              </select>
            </p>
          </div>
          </form>

      <hr>
          <!-- Scene Section -->

          <!-- <Scene v-bind:sceneName="newScene.sceneName" v-bind:bgArray="background_images" v-bind:transitionName="newTransition.transitionName" v-bind:transArray="transitions"></Scene> -->

          <form>
            <p>Scene: 
              <select v-model="newScene.sceneName">
                <option v-for="background_image in background_images">{{ background_image.scene_name }}</option>
              </select>
            </p>

            <p>Transition:  
              <select v-model="newTransition.transitionName">
                <option v-for="transition in transitions">{{ transition.name }}</option>
              </select>
            </p>
          </form>

      <hr>

          <!-- Character Section -->

          <!-- <Character v-bind:firstName="newCharacter.firstName" @change="findCharacterColor()" v-bind:characters="characters" v-bind:dialogue="newDialogue.dialogueText"></Character> -->
          <form>
            <p>Character: <select v-model="newCharacter.firstName" @change="findCharacterColor()">
              <option v-for="character in characters">{{ character.first_name }}</option>
            </select></p>
            <p>Color: <select v-model="newCharacter.color">
              <option v-for="character in characters">
                {{ character.color }}
              </option>
            </select></p>
            <p>Dialogue: <textarea name="dialogue" v-model="newDialogue.dialogueText" rows="2" cols="30"> 
              Enter your character's dialogue...
            </textarea>
            </p>
            <input type="submit" value="Add more dialogue">
          </form>
      <hr>

          <!-- Menu Section -->

          <!-- <Menu v-bind:menuName="newMenu.menuName" v-bind:labelArray="labels" v-bind:introText="newMenu.introText"></Menu>
          <Choice @submit.prevent="addChoice()" v-bind:choiceLabel="newMenu.choiceLabel1" v-bind:labelArray="labels" v-bind:choice="newMenu.choice1"></Choice> -->
            <form>
              <p>Menu: <select name="labels" v-model="newMenu.menuName">
                <option v-for="label in labels">{{ label.name }}</option>
               </select></p>
              <p>Intro line: <input type="text" v-model="newMenu.introText" name="intro_line"></p>
              <p>Choice 1 label: <select name="labels" v-model="newMenu.choiceLabel1">
                <option v-for="label in labels">{{ label.name }}</option>
              </select></p>
              <p>Choice 1 text: <input type="text" name="choice1" v-model="newMenu.choice1"></p>
              <p>Choice 2 label: <select name="labels" v-model="newMenu.choiceLabel2">
                <option v-for="label in labels">{{ label.name }}</option>
              </select></p>
              <p>Choice 2 text: <input type="text" name="choice1" v-model="newMenu.choice2"></p>
              <component v-for="field in fields" v-bind:is="field.type" :key="field.id"></component>
              <button type="button" v-on:click="addFormElement('choice-select')">Add Choice</button>
            </form>
      <hr>
          <button v-on:click="Generate()">Genera draft</button>
            <form v-on:submit.prevent="Generate()"> <!--Generate button-->
              <button type="submit">Generate</button>
            </form>
        </div>
      </div>
    </section>
  </section>
  </div>
  <!--Right segment end-->    
</template>

<script type="x-template" id="choice-select">
  <p>Choice 1 label: <select name="labels" v-model="newMenu.choiceLabel1">
    <option v-for="label in labels">{{ label.name }}</option>
  </select></p>
  <p>Choice 1 text: <input type="text" name="choice1" v-model="newMenu.choice1"></p>
</script>

<script>
import axios from "axios";
import Label from "@/components/Label.vue";
//var choiceSelect = Vue.component('choice-select', {
//  template: '#choice-select'
//
export default {
  data: function() {
    return {
      output: "",
      message: "Hello world!",
      fields: [],
      count: 0,
      characters: [],
      newCharacter: {
        firstName: " ",
        color: " "
      },
      background_images: [],
      newScene: {
        sceneName: " "
      },
      labels: [],
      newLabel: {
        labelName: null
      },
      listOfLabels: [],
      selectedLabels: [],

      transitions: [],
      newTransition: {
        transitionName: " "
      },
      dialogues: [],
      newDialogue: {
        dialogueText: " "
      },
      menu: [],
      newMenu: {
        menuName: " ",
        introText: " ",
        choice1: " ",
        choiceLabel1: " ",
        choice2: " ",
        choiceLabel2: " "
      }
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
      this.listOfLabels = [this.labels]    
    })
  },
  components: {
    Label
  },
  methods: {
    Generate: function() {
      console.log('translating into RenPy syntax');
      console.log(this.selectedLabels);
      var params = {
        input_first_name: this.newCharacter.firstName,
        input_color: this.newCharacter.color,
        input_label_name: this.newLabel.labelName,
        input_scene_name: this.newScene.sceneName,
        input_transition_name: this.newTransition.transitionName,
        input_dialogue: this.newDialogue.dialogueText,
        input_menu: this.newMenu.menuName,
        input_intro: this.newMenu.introText,
        input_choice1_label: this.newMenu.choice1,
        input_choice1: this.newMenu.choiceLabel1,
        input_choice2_label: this.newMenu.choice2,
        input_choice2: this.newMenu.choiceLabel2

      }
      console.log(params)
      axios.post("/api/drafts", params).then(response => {
      this.output = response.data;
      });
    // },
    // setColor: function(event) {
    //   console.log('setting color')
    //   console.log(event);
    },
    findCharacterColor: function() {
      var characterName = this.newCharacter.firstName;
      console.log(this.characters.indexOf(characterName));
    },
    formIsValid: function() {
      return this.newLabel.labelName;
    },
    addLabel: function() {
      this.listOfLabels.push(this.labels)
    }
    // addFormElement: function(type) {
    //   this.fields.push({
    //     'type': type,
    //     id: this.count++
    //   });
  }
};
</script>
