<template>
<div >
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
    <v-btn @click="goToSorted">
     
      Sort by year
      
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
export default class Home extends Vue {
   
     ids =[500,550,100,128,159,200,666,750,560,10];
     sorted_ids:any[]=[];
     sorted_years:any[]=[];
    
    years_list: any[]=[];
    

    getYear (value: any) {
      console.log(value);
      this.years_list.push(value[1]);
      this.sorted_years.push(value[1]);
      this.sorted_ids.push(value[0]);
      console.log(this.ids);
      console.log(this.years_list);
    }
   

    goToSorted() {
        

        console.log(this.sorted_ids);
        console.log(this.sorted_years);
        for( let i=0;i<this.sorted_years.length;i++){
            console.log(this.sorted_ids);
            console.log(this.sorted_years);
            for ( let j=i+1;j<this.sorted_years.length;j++){
                if(this.sorted_years[j]<this.sorted_years[i]){
                    let temp_year = this.sorted_years[i];
                    this.sorted_years[i]=this.sorted_years[j];
                    this.sorted_years[j]=temp_year;
                    let temp_id = this.sorted_ids[i];
                    this.sorted_ids[i]=this.sorted_ids[j];
                    this.sorted_ids[j]=temp_id;
                }
            }
        }
         
        
        
        console.log(this.sorted_ids);
    this.$router.push({ path: 'sorted', query: {
        id_list:this.sorted_ids,
        
    }});
  }
    
}
</script>