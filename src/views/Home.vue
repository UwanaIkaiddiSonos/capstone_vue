<template>
  <div class="home">
    <h1>{{ message }}</h1>
    
    <form> <!--Label form-->
      <p>Scene: <select name="scene">
        <option value="meadow">Meadow</option>
        <option value="work">Work</option>
        <option value="movies">Movies</option>
      </select></p>

      <p>Transition:  <select name="transition">
        <option value="fade">Fade</option>
        <option value="dissolve">Dissolve</option>
        <option value="swipe">Swipe</option>
      </select></p>
    </form>
<hr>
    <form>
      <p>Character: <select name="character">
        <option value="tohru">Tohru</option>
        <option value="yuki">Yuki</option>
        <option value="kyo">Kyo</option>
      </select><br><br>
      Character pose: <select name="character_show">
        <option value="neutral">Neutral</option>
        <option value="happy">Happy</option>
        <option value="sad">Sad</option>
      </select><br>
      Dialogue: <textarea name="dialogue" rows="2" cols="30">
        Enter your character's dialogue...
      </textarea>
      </p>
      <input type="submit" value="Add more dialogue">
    </form>
<hr>

    <form> <!--Menu form-->
      <p>Choice 1 label: <select name="labels">
        <option value="burger">Burger</option>
        <option value="ramen">Ramen</option>
        <option value="tacos">Taco</option>
      </select></p>
      <p>Intro line: <input type="text" name="intro_line"></p>
      <p>Choice 1 text: <input type="text" name="choice1"></p>
      <p>Choice 2 label: <select name="labels">
        <option value="burger">Burger</option>
        <option value="ramen">Ramen</option>
        <option value="tacos">Taco</option>
      </select></p>
      <p>Intro line: <input type="text" name="intro_line"></p>
      <p>Choice 2 text: <input type="text" name="choice1"></p>
      <input type="submit" value="Add Choice">
    </form>
  </div>
</template>

<script>
  import axios from "axios"
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  data: function() {
    return {
      message: "Hello world!",
      characters: [],
      newCharacter: {
        first_name: "",
        last_name: "",
        color: "",
      }


    };
  }
}
</script>
