<template>
    <div >
    <v-container >
       
    <div v-for="i in 5" :key="i" >
         <v-row no-gutters>
      <v-col
        cols="12"
        sm="6"
      >
        <AlbumInfo :id="sorted_id_list[i-1]" v-on:sendYear="getYear" />
        
       </v-col>
       <v-col
        cols="12"
        sm="6"
      >
        <AlbumInfo :id="sorted_id_list[i+4]" v-on:sendYear="getYear" />
        
       </v-col>
        </v-row> 
    </div>
      
    </v-container>
     <v-btn >
     <router-link to="/" >
     Back
     </router-link>
    </v-btn>
    
</div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';
import AlbumInfo from '@/components/AlbumInfo.vue'

@Component({
  components: {
    AlbumInfo,
  }
})
export default class SortedCards extends Vue {
    sorted_id_list:any;
    
    
    created(){
        
        this.sorted_id_list=this.$route.query.id_list;
       
        
        console.log(this.sorted_id_list);
        
        
    }

    
}
</script>