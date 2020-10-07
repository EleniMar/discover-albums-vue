<template>
 <v-container >
       
    <div v-for="i in 5" :key="i" >
         <v-row no-gutters>
      <v-col
        cols="12"
        sm="6"
      >
        <AlbumInfo :id="ids[i-1]" v-on:sendYear="getYear" />
        
       </v-col>
       <v-col
        cols="12"
        sm="6"
      >
        <AlbumInfo :id="ids[i+4]" v-on:sendYear="getYear" />
        
       </v-col>
        </v-row> 
    </div>
      
    </v-container>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';
import axios from 'axios';
import AlbumInfo from '@/components/AlbumInfo.vue'

@Component({
  components: {
    AlbumInfo,
  }
})
export default class AlbumList extends Vue {
    @Prop({required: true}) readonly ids: any;
}
</script>