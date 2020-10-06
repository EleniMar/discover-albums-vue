<template>
<div class="container text-center">

<v-container class="grey lighten-5 text-center">
    <v-row no-gutters>
      <v-col
        cols="12"
        sm="6"
      >
        <Card :key="cardKey"/>
      </v-col>
      <v-col
        cols="12"
        sm="6"
      >
      <v-card
      class="d-flex grey lighten-5 align-content-center flex-wrap"
      elevation="0"
      min-height="200"
    >
      <v-card
        class="pa-2 grey lighten-5"
        elevation="0"
      ><v-card-title>Discover another album!</v-card-title>
         <v-btn
      class="mx-2"
      fab
      dark
      large
      color="purple"
      @click="reload"
    >
      <v-icon class="ma-3" @click="forceRerender">
        autorenew
      </v-icon>
    </v-btn>
    
      </v-card>
    </v-card>
      
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
},
data() {
    return {
      cardKey: 0,
    };
  },
  methods: {
    forceRerender() {
      this.cardKey += 1;
    }
  }
})
</script>

<style>
.content {
  display: flex;
  justify-content: center;
}

.details-card {
  max-width: 800px;
  padding: 1rem 2rem;
}

.details-card p {
  padding-left: 2rem;
}
</style>