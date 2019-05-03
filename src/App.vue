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
            <li><a href="/about">About</a></li>
            <li><a href="/new">New</a></li>
            <li><a href="portfolio.html">Portfolio</a></li>
            <li><a href="blog.html">Journal</a></li>
            <li><a href="contact.html">Contact</a></li>
            <li><a href="shortcodes.html">Shortcodes</a></li>
            <li class="menu-item-has-children"><a href="index.html">Submenu</a>
              <ul class="sub-menu">
                  <li><a href="#">Item 1</a></li>
                  <li><a href="#">Item 2</a></li>
                  <li><a href="#">Item 3</a></li>
                  <li><a href="#">Item 4</a></li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </div>
  <!-- Menu end-->
    <div class="wrapper">
    <!-- Hero section-->
      <section class="split-image parallax" data-background="assets/images/module-7.jpg">
        <div class="split-image-footer">
          <ul class="split-list">
            <li>Download cv:</li>
            <li><a href="#">English</a></li>
            <li><a href="#">German</a></li>
            <li><a href="#">Spanish</a></li>
          </ul>
        </div>
      </section>
    <!-- Hero section end-->
    <!-- Content section-->
      <section class="split-content">
        <!-- Hello text-->
        <section class="module">
          <div class="container-fluid container-custom">
            <div class="row">
              <div class="col-sm-12">
                <h1>Hello, I am Robert Fields<br>Designer and Front-end Developer.</h1>
                  <p>Exercitation photo booth stumptown tote bag Banksy, elit small batch freegan sed. Craft beer elit seitan exercitation, photo booth et 8-bit kale chips proident chillwave deep v laborum. Aliquip veniam delectus, Marfa eiusmod Pinterest in do umami readymade swag.</p>
              </div>
            </div>
          </div>
        </section>
        <!-- Hello text end-->
      </section>
    </div>
    <router-view/>
      <footer class="footer">
        <div class="container-fluid container-custom">
          <div class="row">
              <div class="col-md-7">
                <p>© 2016 Node. All rights reserved</p>
              </div>
              <div class="col-md-5">
                <ul class="social-list">
                  <li><a href="#"><i class="fa fa-twitter"></i></a></li>
                  <li><a href="#"><i class="fa fa-facebook"></i></a></li>
                  <li><a href="#"><i class="fa fa-google-plus"></i></a></li>
                  <li><a href="#"><i class="fa fa-linkedin"></i></a></li>
                </ul>
              </div>
          </div>
        </div>
      </footer>    
  </div>
</template>

<style>

</style>
