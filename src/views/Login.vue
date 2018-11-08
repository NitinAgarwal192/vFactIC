<template>
  <div id="app">
  <v-app id="inspire">
    <v-form>
      <v-container>
        <v-layout row wrap class="text-xs-center text-lg-center text-md-center text-sm-center">
          <v-flex xs12 sm12 md12>
            <h1>Softvent</h1>
            <p class="sub-title">Login</p>
            <v-flex class="pa-4">
            <v-text-field
              color="light-blue"
              label="User Name"
              v-model="userName"
            ></v-text-field>
            <v-text-field
            v-model="userPassword"
              color="light-blue"
              label="Password"
              type="password"
            ></v-text-field>
            </v-flex>
            <v-btn outline small fab color="green" @click="createWindow">
              <v-icon>check</v-icon>
            </v-btn><span>Login</span>
            <v-btn outline small fab color="red">
              <v-icon>close</v-icon>
            </v-btn><span>Cancel</span>
          </v-flex>
          <v-flex xs12 sm12 md12>
            <p class="footer-text">Forget your Password ?</p>
          </v-flex>
        </v-layout>
      </v-container>
    </v-form>
  </v-app>
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

<style scoped>
.sub-title {
  font-size: 1.3rem;
}
.sub-title {
  font-size: 30px;
}
.hello {
  margin-top: 3%;
}
.footer-text {

}
</style>