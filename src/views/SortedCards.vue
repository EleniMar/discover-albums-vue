<template>
    <div >
   <AlbumList :ids="sorted_id_list" />
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
import AlbumList from '@/components/AlbumList.vue'

@Component({
  components: {
    AlbumList,
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