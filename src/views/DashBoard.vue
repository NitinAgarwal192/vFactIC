<template>
  <div id="dashboard">
    <v-app id="inspire">
        <v-layout fill-height>
          <v-flex xs4>
            <SideBar/>
          </v-flex>
          <v-flex xs8>
            <router-view/>
          </v-flex>
        </v-layout>
    </v-app>
  </div>
  <!-- <div class="dashboard">
    <h1>DashBoard</h1>
    <div id="sidebar">

    </div>
    <div id="main-view">

    </div>
    <SideBar/>
    <router-view/>
  </div> -->
</template>

<script>
import SideBar from './DashBoard/SideBar.vue'
export default {
  name: 'home',
  components: {
    SideBar
  },
}
</script>

<style scoped>
.dashboard {
  height: 100%;
}
</style>
