<template>

<v-list
        
      subheader
      three-line>
            <v-list-item-group
         
          color="primary"
        >
          <v-list-item
            v-for="i in 10"
            v-bind:key="i"
           
          >
        
            
               <Card />
           
          </v-list-item>
        </v-list-item-group>
        </v-list>

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