<template>
  <div id="app">
    <!--<Skills /> -->
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <!--<div>
      <table>
      <tr>
      <td><span class="homeBar"></span></td>
      <td><span class="aboutBar"></span></td>
      </tr>
      </table>
    </div>-->
    <router-view/>
  </div>
</template>

<script>
//import Skills from './components/Skills.vue'

export default {
  name: 'app'//,
  //components: {
    //Skills
  //}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');

body {
  background-color: #EEEEEE;
  font-family: 'Montserrat', sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  /*align-items: center;*/
  padding-top: 50px;
}
body, html {
  margin: 0;
  height: 100%;
}
#app {
    width: 50%;
}

nav {
  padding: 20px 20px 20px 0;
}

nav a {
  padding: 10px;
  text-decoration: none;
  /*background: #fff;*/
  background:blue;
  border-radius: 3px;
  /*color: rgb(0, 110, 255);*/
  color: white;
  font-weight: bold;
  margin-right: 15px;
}

.router-link-exact-active{
  background: lightgray;
  color: grey;
  cursor:default;
  pointer-events: none;
}

/*.homeBar{
  padding: 5px;
  background: blue;
  margin-left: 0px;
  display: block;
  width: 60px;
}
.aboutBar{
  padding: 5px;
  background: blue;
  margin-left: 8px;
  display: block;
  width: 60px;
}*/
</style>
