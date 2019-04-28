<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <form> <!--Label form-->
      <p>Scene: <select>
        <option v-for="scene in background_images">{{ background_image.url }}</option>
      </select></p>

      <p>Transition:  <select name="transition">
        <option value="fade">Fade</option>
        <option value="dissolve">Dissolve</option>
        <option value="swipe">Swipe</option>
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
        <option value="burger">Burger</option>
        <option value="ramen">Ramen</option>
        <option value="tacos">Taco</option>
      </select></p>
      <p>Choice 1 text: <input type="text" name="choice1"></p>
      <p>Choice 2 label: <select name="labels">
        <option value="burger">Burger</option>
        <option value="ramen">Ramen</option>
        <option value="tacos">Taco</option>
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
        first_name: "",
        last_name: "",
        color: ""
      },
      background_images: [],
      newBackgroundImage: {
        url: ""
      }
    };
  },
  created: function() {
    axios.get("/api/characters").then(response => {
      this.characters = response.data;
    });
    axios.get("/api/background_images").then(response => {
      this.background_images = response.data;    
    })
  },
};
</script>
