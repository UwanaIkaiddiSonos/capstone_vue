<template>
  <div class="home">
    <h1>{{ message }}</h1>
    
    <form>
      <p>Intro line: <input type="text" name="intro_line"></p>
      <p>Choice 1 text: <input type="text" name="choice1"></p>
      <input type="submit" value="Add choice menu">
    </form>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  data: function() {
    return {
      message: "Hello world!",
      characters: []
    };
  }
}
</script>
