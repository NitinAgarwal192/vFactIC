<template>
    <div id="trial">
        <h1>This is called jogad</h1>
        <button @click="createWindow">login</button>
    </div>
</template>

<script>
import {ipcRenderer} from 'electron'

export default {
  name: 'LoginScreen',
  data: function() {
    return {
      userName: null,
      userPassword: null
    }
  },
  methods: {
    createWindow() {
      var _windowProperties = {
        state : 1,
        message : "Error message send",
        windowProperty : {maximizable:true},
        router: "dashboard"
      }
      ipcRenderer.send('open-dashboard-window', _windowProperties)
    }
  }
}
</script>