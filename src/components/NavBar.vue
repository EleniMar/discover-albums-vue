<template>

    <v-app-bar dense fixed>
      

      <v-toolbar-title class="ma-2" @click="reload"><router-link to="/" >Title</router-link></v-toolbar-title>
      <router-link to="/" ><v-icon class="ma-2 dark">home</v-icon></router-link>

      <v-btn
      class="ma-2"
      outlined
      color="indigo"
      
    ><router-link to="/random" > 
      RANDOM ALBUM
      </router-link>
    </v-btn>

     <div class="text-center">
    <v-menu
      open-on-hover
      top
      offset-y
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Dropdown
        </v-btn>
      </template>

      <v-list>
        <v-list-item
          v-for="(item, index) in items"
          :key="index"
        >
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
  </div>

      <v-spacer></v-spacer>

      
    </v-app-bar>
  
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    data: () => ({
      items: [
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me 2' },
      ],
    })
  
    
  
})
</script>

