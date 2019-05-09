<template>
  <div class="wrapper">
  <!--Left segment-->
  <section class="split-image parallax" data-background="assets/images/girl_reading.jpg">
    <div class="container-fluid container-custom">
      <br><br>
        <div class="center">
          <textarea readonly name="final" rows="20" cols="60">{{ output['output'] }}</textarea>
        </div>
    </div>
  </section>
  <!--Left segment end-->
  <!--Right segment-->
  <section class="split-content">
    <!--Insert content here-->
    <section class="module">
      <div class="container-fluid container-custom">
        <div class="row">
          <div class="col-sm-12">
            <div class="test">
              <!-- Instructions -->
              <div class="center">
                <h1>EasyPy Converter</h1>
              </div>
                <h3>Instructions</h3>
                <ol>
                  <li>Start by adding a <button class="btn-sm" v-on:click="addField('Character')">Character</button></li>
                  <li>Then add a <button class="btn-sm" v-on:click="addField('Label')">Path</button></li>
                  <li>Set up the <button class="btn-sm" v-on:click="addField('Scene')">Scene</button> and <button class="btn-sm" v-on:click="addField('Transition')">Transition</button></li>
                  <li>Add a <button class="btn-sm" v-on:click="addField('CharacterImage')">Character Image</button></li>
                  <li>Throw in some <button class="btn-sm" v-on:click="addField('Dialogue')">Dialogue</button></li>
                  <li>End with a <button class="btn-sm" v-on:click="addField('Menu')">Choice</button></li>
                </ol>
              <form>
              <!-- Label Section -->
              <!-- <button v-on:click.prevent="addLabel()">Add new label dropdown</button> -->
                <!-- <div v-for="oneLabel, $index in listOfLabels"> -->
              <!-- </div> -->
              </form>
              <hr class="new1">
              <!-- <button v-on:click="addField('Label')">Path</button>
              <button v-on:click="addField('Transition')">Transition</button>
              <button v-on:click="addField('Character')">Character</button>
              <button v-on:click="addField('Scene')">Scene</button>
              <button v-on:click="addField('Dialogue')">Dialogue</button>
              <button v-on:click="addField('Menu')">Choice</button>
              <button v-on:click="addField('CharacterImage')">Character Image</button> -->
              <div v-for="input in arrayOfFieldInputs">
                

                <div v-if="input.type === 'Label'">
                  <p>Path:  
                  <select v-model="input.userInput">
                    <option v-for="label in labels">{{ label.name }}</option>
                  </select></p>
                  <hr>
                </div>
                <div v-if="input.type === 'Transition'">
                  <p>Transition:  
                      <select v-model="input.userInput" v-on:change="printArray()">
                        <option v-for="transition in transitions">{{ transition.name }}</option>
                      </select>
                  </p>
                  <hr>
                </div>
                <div v-if="input.type === 'Character'">
                  <p>Character:  
                      <select v-model="input.userInput" v-on:change="printArray()">
                        <option v-for="character in characters">{{ character.first_name }}</option>
                      </select>
                  </p>
                  <p>Color:
                    <input type="color" v-model="input.color">
                  </p>
                  <hr>
                </div>
                <div v-if="input.type === 'CharacterImage'">
                  <p>Character Image:  
                    <select v-model="input.userInput" v-on:change="printArray()">
                      <option v-for="image in images">{{ image.name }}</option>
                    </select>
                  </p>
                  <hr>
                </div>
                <div v-if="input.type === 'Scene'">
                  <p>Scene:  
                      <select v-model="input.userInput" v-on:change="printArray()">
                        <option v-for="scene in background_images">{{ scene.scene_name }}</option>
                      </select>
                  </p>
                  <hr>
                </div>
                <div v-if="input.type === 'Dialogue'">
                  Speaker: <select v-model="input.character" v-on:change="printArray()">
                    <option v-for="character in characters">{{ character.first_name }}</option>
                  </select><br>
                  <p>Dialogue: <input type="text" v-model="input.userInput" rows="2" cols="30"> 
                </input>
                </p>
                <hr>
              </div>
              <div v-if="input.type === 'Menu'">
                <p>Choice Menu: </p>
                <p>Intro line: <input type="text" v-model="input.intro" name="intro_line"></p>
                <p>Choice 1 text: <input type="text" name="choice1" v-model="input.choice1"></p>
                <p>Choice 1 label: <select name="labels" v-model="input.choice1_label">
                  <option v-for="label in labels">{{ label.name }}</option>
                </select></p>
                <p>Choice 2 text: <input type="text" name="choice1" v-model="input.choice2"></p>
                <p>Choice 2 label: <select name="labels" v-model="input.choice2_label">
                  <option v-for="label in labels">{{ label.name }}</option>
                </select></p>
                <hr>
              </div>
            </div>
            <input class="btn-lg" type="submit" value="Generate" v-on:click="Generate()">
          </div>
        </div>
      </div>
      </div>
    </section>
  </section>
  </div>
  <!--Right segment end-->    
</template>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      output: "",
      message: "Hello world!",
      characters: [],
      newCharacter: {
        firstName: " ",
        color: " "
      },
      images: [
        {
          name: "sylvie green normal"
        },
        {
          name: "sylvie green smile"
        },
        {
          name: "sylvie green giggle"
        },
        {
          name: "sylvie green surprised"
        }
      ],
      background_images: [],
      newScene: {
        sceneName: " "
      },
      // listOfScenes: [],
      // selectedScenes: [],

      // listOfTransitions: [],
      // selectedTransitions: [],

      labels: [],
      newLabel: {
        labelName: null
      },
      // listOfLabels: [],
      // selectedLabels: [],

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
      },
      arrayOfFieldInputs: [],
    };
  },
  created: function() {
    axios.get("/api/characters").then(response => {
      this.characters = response.data;
    });
    axios.get("/api/background_images").then(response => {
      this.background_images = response.data;
      // this.listOfScenes = [this.background_images]    
    });
    axios.get("/api/transitions").then(response => {
      this.transitions = response.data;
      // this.listOfTransitions = [this.transitions]    
    });
    axios.get("/api/labels").then(response => {
      this.labels = response.data;
      // this.listOfLabels = [this.labels]    
    })
  },
  methods: {
    Generate: function() {
      // console.log('translating into RenPy syntax');
      // console.log(this.arrayOfFieldInputs);
      var params = {
        fieldInputs: this.arrayOfFieldInputs
      }
      axios.post("/api/drafts", params).then(response => {
        this.output = response.data;
      });
    },
    findCharacterColor: function() {
      var characterName = this.newCharacter.firstName;
      // console.log(this.characters.indexOf(characterName));
    },
    formIsValid: function() {
      return this.newLabel.labelName;
    },
    addField: function(fieldType) {
      // console.log(fieldType);
      if (fieldType === 'Dialogue') {
        this.arrayOfFieldInputs.push({type: fieldType, userInput: "", character: ""});
      }
      else if (fieldType === 'Menu') {
        this.arrayOfFieldInputs.push({type: fieldType, intro: "", choice1: "", choice1_label: "", choice2: "", choice2_label: ""});
      }
      else if (fieldType === 'Character') {
        this.arrayOfFieldInputs.push({type: fieldType, userInput: "", color: ""})
      }
      else {
        this.arrayOfFieldInputs.push({type: fieldType, userInput: ""});
      }
      // console.log(this.arrayOfFieldInputs);
    },
    printArray: function() {
      console.log(this.arrayOfFieldInputs);
    }
    // addLabel: function() {
    //   this.listOfLabels.push(this.labels);
    // },
    // addScene: function() {
    //   this.listOfScenes.push(this.background_images);
    // },
    // addTransition: function() {
    //   this.listOfTransitions.push(this.transitions);      
    // }
  }
};
</script>
