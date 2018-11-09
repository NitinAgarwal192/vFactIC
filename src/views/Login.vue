<template>
  <div id="app">
  <v-app id="inspire">
    <v-form>
      <v-container>
        <v-layout row wrap class="text-xs-center text-lg-center text-md-center text-sm-center">
          <v-flex xs12 sm12 md12>
            <p class="heading">Softvent</p>
            <p class="sub-title">Login</p>
            <v-flex xs6 sm6 md6 offset-xs3 class="pa-4">
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
            <v-flex>
              <v-btn outline small fab color="green" @click="validateAuthUser">
                <v-icon>check</v-icon>
              </v-btn><span class="btn-text">Login</span>
              <v-btn outline small fab color="red">
                <v-icon>close</v-icon>
              </v-btn><span class="btn-text">Cancel</span>
            </v-flex>
          </v-flex>
          <!-- <v-flex xs12 sm12 md12>
            <p class="footer-text">Forget your Password ?</p>
          </v-flex> -->
        </v-layout>
      </v-container>
    </v-form>
      <v-snackbar
        v-model="snackbar"
        :bottom="'bottom'"
        :timeout="timeout"
        :color="'red'"
      >
        {{ snackbartext }}
        <v-btn
          color="black"
          flat
          @click="snackbar = false"
        >
          Close
        </v-btn>
      </v-snackbar>
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
      userPassword: null,
      snackbar: false,
      timeout: 2000,
      snackbartext: 'Error'
    }
  },
  methods: {
    validateAuthUser() {
      let userid = this.userName;
      let password = this.userPassword;
      if(!userid){
        this.snackbartext = 'Enter the user name';
        this.snackbar = true;
      }else if(!password) {
        this.snackbartext = 'Enter the user password';
        this.snackbar = true;
      } else {
        this.AuthUser(userid,password);
      }
    },
    AuthUser(userid,password) {
      if(userid === 'admin' && password === 'admin'){
        this.createWindow();
      } else {
        this.snackbartext = 'Invalid Credentials';
        this.snackbar = true;
      }
    },
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
.heading {
  font-weight: 500;
  font-size:  2.7rem;
}
.sub-title {
  font-size: 1.9rem;
  font-weight: 200;
}
.hello {
  margin-top: 3%;
  font-weight: 100;
}
.btn-text {
  font-weight: 200;
}
.footer-text {

}
</style>