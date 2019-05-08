<template>
  <div id="app">
  <!-- Show menu-->
    <div class="show-menu-btn">
      <span></span>
      <span></span>
      <span></span>
    </div>
  <!-- Show menu end-->
  <!-- Menu-->
    <div class="overlay-menu">
      <div class="menu-table">
        <div class="menu-table-cell">
          <ul class="navigation">
            <li><a href="/">Home</a></li>
            <!-- <li><a href="/about">About</a></li> -->
            <li><a href="/new">Characters</a></li>
          </ul>
        </div>
      </div>
    </div>
  <!-- Menu end-->
    <router-view/>  
  </div>
</template>

<style>
  @import url('https://fonts.googleapis.com/css?family=Suranna');
</style>
