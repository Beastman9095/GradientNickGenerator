<template>
  <div class="body">
    <div class="input">
      <header>
        <div class="container2">
          <a href="https://discord.gg/ham5teak">
            Discord
          </a>
          <a href="https://shop.ham5teak.xyz/">
            Shop
          </a>
          <h1>Minecraft Gradient Nickname Generator</h1>
          <a href="https://ham5teak.xyz/">
            Forums
          </a>
          <a href="https://ham5teak.xyz/pages/vote/">
            Vote
          </a>
        </div>
      </header>
      <header>
        <input v-model="username" @change="log()" style="color: #151718;" type="text" placeholder="Input Username Here" id="username">
        <br>
        <br>
        <p>Output is: </p>
        <div class="output">
          <p2 id='p2'>{{ username }}</p2>
        </div>
        <br>
        <br>
        <p>Nick Format: </p>
        <div class="cmiformat">
          <p3>{{ cmiformat }}</p3>
        </div>
      </header>
    </div>
    <form action="action_page.php" method="post" id="a">
    <div class="container">
      <div class="user">
        <label for="firstcolor">Select the first color:</label>
        <form action="/action_page.php">
          <br>
          <input v-model="firstcolor" @change="log()" type="color" id="firstcolor" name="firstcolor" value="#00FFFF">
        </form>
      </div>
      <div class="checkboxes">
        <form action="/action_page.php">
          <label for="bold">Bold</label>
          <input v-model="bold" @change="log()" type="checkbox" id="checkbox" name="checkbox">
        </form>
      </div>
      <div class="password">
        <label for="secondcolor">Select the second color:</label>
        <form action="/action_page.php">
          <br>
          <input v-model="secondcolor" @change="log()" type="color" id="secondcolor" name="secondcolor" value="#00FFFF">
        </form>
      </div>
    </div>
  </form>
  <br>
  <br>
  <div class="footer">
    <footer>
      ℗ Copyright Ham5teak
      <br>
      <br>
      Developer: Beastman
    </footer>
  </div>
  </div>
</template>

<script>
import chroma from 'chroma-js'
export function sc (color1, color2, word, bold) {
  var letters = Array.from(word)
  var num = letters.length
  var colors = chroma.scale([color1, color2]).mode('lch').colors(num)
  var str = ''
  if (String(bold) === 'true' || String(bold) === 'True') {
    for (var b = 0; b <= num - 1; b++) {
      str += '{' + `${colors[b]}` + '}' + `&l${letters[b]}`
    }
    var dom2 = document.getElementById('p2')
    dom2.style.fontWeight = 'bold'
  } else {
    for (var i = 0; i <= num - 1; i++) {
      str += '{' + `${colors[i]}` + '}' + `${letters[i]}`
    }
    var dom1 = document.getElementById('p2')
    dom1.style.fontWeight = 'normal'
  }
  return str
}
export default {
  name: 'Login',
  data () {
    return {
      username: 'Text Here',
      firstcolor: '#C2DACB',
      secondcolor: '#C2DACB',
      cmiformat: '',
      bold: 0
    }
  },
  methods: {
    log () {
      this.cmiformat = sc(this.firstcolor, this.secondcolor, this.username, this.bold)
      var dom = document.getElementById('p2')
      dom.style.backgroundImage = `linear-gradient(to right, ${this.firstcolor}, ${this.secondcolor})`
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
.container {
  display: grid;
  grid-gap: 50px 100px;
  padding-inline: 15%;
  width: 70%;
  padding-top: 30px;
  margin-bottom: 2%;
}
.psw {
  text-decoration-line: underline;
  font-size: small;
  font-weight: bold;
  color: #42b983;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 10px;
}
a {
  text-decoration-line: underline;
  font-size: larger;
  font-weight: bold;
  color: #42b983;
}
b {
  text-decoration-line: none;
  font-size: medium;
  font-weight: bold;
  margin: 5px;
}

.container .user{
  grid-column-start: 1;
  grid-column-end: 1;
}

.container .checkboxes{
  grid-column-start: 2;
  grid-column-end: 2;
}

.container .checkboxes label{
  vertical-align: middle;
  height: 100px;
  line-height: 100px;
}

.container .checkboxes input{
  background-color: #151718;
  vertical-align: middle;
  height: 80px;
  line-height: 80px;
}

.container .checkboxes input:focus{
  vertical-align: middle;
  height: 80px;
  line-height: 80px;
  width: 25px;
  height: 25px;
}

.container .password{
  grid-column-start: 3;
  grid-column-end: 3;
}

.input input {
  margin-top: 8% !important;
  font-size: 20px;
  width: 200px;
  height: 25px;
  padding: 10px 10px;
  border: 2px solid #3D4446;
  border-radius: 4px;
  background-color: #151718;
  color: #C2DACB;
  resize: none;
  transition: 0.2s;
}

p2 {
  text-align: center !important;
  font-size: 25px;
  background-image: linear-gradient(to right, rgb(0, 204, 255), green);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  resize: none;
  transition: 0.2s;
}

p3 {
  color: #C2DACB;
  font-size: 15px;
  resize: none;
  transition: 0.2s;
  overflow-wrap: break-word;
}

.cmiformat {
  border: 2px solid #3D4446;
  display: inline-block;
  border-radius: 4px;
  padding: 2%;
  max-width: 50%;
  white-space: pre-wrap;
  word-wrap: break-word;
}

.input input:hover {
  padding: 10px 10px;
  width: 300px;
  height: 50px;
}

.input input:focus {
  width: 300px;
  height: 50px;
}

.container input {
  width: 25px;
  height: 25px;
  padding: 10px 10px;
  border: 2px solid #3B4244;
  border-radius: 4px;
  background-color: #151718;
  resize: none;
  transition: 0.2s;
}

.container input:hover {
  padding: 10px 10px;
  width: 50px;
  height: 50px;
}

.container input:focus {
  width: 50px;
  height: 50px;
}

.container .user .InputText input {
  width: 150px;
  height: 30px;
  padding: 10px 10px;
  border: 2px solid #3D4446;
  border-radius: 4px;
  background-color: #363636c4;
  resize: none;
  transition: 0.2s;
}

.container .user .InputText input:hover {
  width: 200px;
  height: 70px;
}
.output {
  src: url("//db.onlinewebfonts.com/t/6ab539c6fc2b21ff0b149b3d06d7f97c.eot");
  font-family: 'Minecraft';
  font-weight: normal;
  font-style: normal;
  border: 2px solid #3D4446;
  display: inline-block;
  border-radius: 4px;
  padding: 2%;
  max-width: 50%;
  white-space: pre-wrap;
  word-wrap: break-word;
}

.container .user .InputText input:focus {
  width: 200px;
  height: 70px;
}

label {
  color: #C2DAEE;
}

p {
  color: #C2DAEE;
}

h1 {
  color: #C2DAEE;
}

.container2 {
  position: fixed;
  display: flex;
  align-items: center;
  width: 100%;
  height: 15%;
  background: #151718;
  top: 0px;
  left: 0px;
  display: grid;
  padding: -10px;
  grid-template-columns: repeat(5, 5fr);
  gap: 2.5px;
}

.container2 a{
  position: relative;
  font-size: 20px;
  text-decoration-line: none;
  transition: 0.05s;
}

.container2 h1{
  color: #C2DAEE;
  font-size: 2.5px;
  font-size: 1.75vw;
  resize: both;
  text-decoration-line: none;
  transition: 0.1s;
  line-height: 25px;
  text-align: center;
}

.container2 a:hover{
  color: #3aa374;
  font-size: 25px;
}

.footer {
  width: 100%;
  right: 0px;
  padding-bottom: 20px;
  color: #C2DAEE;
}

input {
  background: #151718;
  color: #C2DAEE !important;
  text-align: center !important;
}

@media only screen and (max-width: 600px) {
  .container2 {
    position: relative;
    display: flex;
    align-items: center;
    font-size: 2.5px;
    font-size: 1.75vw;
    width: 100%;
    background: #151718;
    display: grid;
    grid-template-columns: repeat(5, 5fr);
    gap: 2.5px;
  }
  .container2 a {
    font-size: 2.5px;
    font-size: 2.5vw;
    resize: both;
  }

  .container2 a:hover{
    color: #3aa374;
    font-size: 20px;
  }
  .container2 h1 {
    font-size: 2px;
    font-size: 2vw;
    resize: both;
  }
}

html[data-theme='dark'] {
  scroll-behavior: smooth;
}
</style>
