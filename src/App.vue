<template>
  <div id="app">
<v-app>
  
    <NavBar />
  

  <!-- Sizes your content based upon application components -->
  <v-main>

    <!-- Provides the application the proper gutter -->
    <v-container fluid>

      <!-- If using vue-router -->
      <router-view ></router-view>
    </v-container>
  </v-main>

 
    <Footer />
  
</v-app>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import NavBar from "@/components/NavBar.vue"
import Footer from "@/components/Footer.vue"


export default Vue.extend({
  components: {
    NavBar,
    Footer,
    
  },
  
})
</script>

<style>
#app {
  font-family: Roboto,Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
