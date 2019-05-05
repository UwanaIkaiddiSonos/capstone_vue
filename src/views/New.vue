<template>
      <div class="wrapper">
    <!-- Left segment-->
      <section class="split-image parallax" data-background="assets/images/module-7.jpg">
        <!-- Insert content here -->
      </section>
    <!-- Left segment end-->
    <!-- Right segment-->
      <section class="split-content">
        <!-- Insert content here-->
        <section class="module">
          <div class="container-fluid container-custom">
              <div class="new">
                <h1>{{ message }}</h1>

                <form> <!--Character form-->
                  <p>First Name: <input type="text" v-model="newCharacter.firstName"></p>
                  <p>Last Name: <input type="text" v-model="newCharacter.lastName"></p>
                  <p>Color: <input type="color" v-model="newCharacter.color"></p>
                <button v-on:click.prevent="addCharacter()">Create character</button>
                </form>
            <hr>
                <form> <!--Label form-->
                  <p>Scene Name: <input type="text" v-model="newScene.sceneName"></p>
                  <button v-on:click.prevent="addScene()">Create scene</button>
                </form>
            <hr>
                <form> <!--Label form-->
                  <p>Label Name: <input type="text" v-model="newLabel.name"></p>
                  <button v-on:click.prevent="addLabel()">Create label</button>
                </form>
            <hr>
              </div>
          </div>
        </section>
        <!-- Hello text end-->
      </section>
    </div>
    <!-- Right segment end-->
</template>

<script>
import axios from "axios";
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue';

export default {
  data: function() {
    return {
      message: "Hello world!",
      newCharacter: {
        firstName: "",
        lastName: "",
        color: "#000000"
      },
      newScene: {
        sceneName: ""
      },
      newLabel: {
        name: ""
      }
    };
  },
  methods: {
    addCharacter: function() {
      console.log('adding character');
      var params = {
        input_first_name: this.newCharacter.firstName,
        input_last_name: this.newCharacter.lastName,
        input_color: this.newCharacter.color
      }
      axios.post("/api/characters", params).then(response => {
        console.log(response);
      });
    },
    addScene: function() {
      console.log('adding scene');
      var params = {
        input_scene_name: this.newScene.sceneName
      }
      console.log(this.newScene.sceneName)
      axios.post("/api/background_images", params).then(response => {
        console.log(response);
      });
    },addLabel: function() {
      console.log('adding label');
      var params = {
        input_name: this.newLabel.name,
      }
      axios.post("/api/labels", params).then(response => {
        console.log(response);
      });
    },
  }
};
</script>
