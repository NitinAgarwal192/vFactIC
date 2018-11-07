<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <button @click="createWindow">create</button>
  </div>
</template>

<script>
import {ipcRenderer} from 'electron'

export default {
  name: 'home',
  components: {
  
  },
  methods: {
    createWindow() {
      var _windowProperties = {
        state : 1,
        message : "Error message send",
        windowProperty : {width: 500, height: 500},
        router: "about"
      }
      ipcRenderer.send('open-dashboard-window', _windowProperties)
    }
  }
}
</script>
