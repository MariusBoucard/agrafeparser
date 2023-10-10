<template>
  <h1>Colle ici le code venant directement de BeeFree</h1>
  <p>And don't forget to stay alive</p>
  <p>Ensuite, il y a juste à selectionner l'affichage à droite, ctrl+c, ctrl+v et roulez jeunesse</p>
<div class="container">

  <div class="text-area">
    <textarea placeholder="Enter your text here" v-model="html"></textarea>
  </div>
  
<div class="output">
  
  <HelloWorld 
  :html=this.html
  />
</div>
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data(){
    return {
      html : ""
    }
  }
}
</script>

<style>
body{
  background-color: #ccc;
}
.text-area {
  margin: 20px;
}
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  height: 80vh;
}
textarea {
  width: 100%;
  height: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  resize: vertical;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
