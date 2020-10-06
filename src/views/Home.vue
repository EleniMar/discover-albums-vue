<template>
  <div class="search" >
    
    <h2>Discover new releases!</h2>
      <v-container class="grey lighten-5">
    <v-row no-gutters>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
    </v-row>

    <v-row no-gutters>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
    </v-row>

    <v-row no-gutters>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
       
    </v-row>
    <v-row no-gutters>
      <v-col
        cols="12"
        sm="4"
      >
       
      </v-col>
      <v-col
        cols="12"
        sm="4"
      >
        <Card />
      </v-col>
      <v-col
        cols="12"
        sm="4"
      >
      
      </v-col>
       
    </v-row>
  </v-container>
        
      
 
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Card from '@/components/Card.vue'
export default Vue.extend({
  components:{
  Card
}
})
</script>


<style>
.input-group {
  margin-top: 1rem;
  display: flex;
  justify-content: center;
}

.input-group-field {
  margin-right: 0;
}

.input-group .input-group-button {
  margin-left: 0;
  border: none;
}

.input-group .md-raised {
  margin-top: 0;
  margin-bottom: 0;
  border-radius: 0;
}
</style>

