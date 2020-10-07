<template>
<div class="container text-center">

<v-container class="grey lighten-5 text-center">
    <v-row no-gutters>
      <v-col
        cols="12"
        sm="6"
      >
        <div class="card"   >
    <v-card
    
    class="mx-auto my-12 grey lighten-5 text-center"
    max-width="374"
    elevation="0"
  >
    
    <v-card-text>
      <h2 class=" text--primary">
        {{album.title}}
        </h2>
        <h3>
        <strong>Artist: </strong>
        {{album.artist}}
        </h3>

      <div><p><strong>Year: </strong>{{album.year}}</p></div>
       <div><p><strong>Genre: </strong>{{album.genres}}</p></div>
       <div><p><strong>Country: </strong>{{album.country}}</p></div>


    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-text>
        <div>
             <h3>
        <strong>Tracklist: </strong>
             </h3>
            
          <h5
            v-for="track in album.tracklist"
            :key="track.key"
           
          >

            
              {{track.key}} {{track}}
            
          </h5>
        
        </div>

    </v-card-text>


  </v-card>
        </div>
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
      ><v-card-title>Gallery</v-card-title>
      
  <v-carousel v-model="model">
    <v-carousel-item
      v-for="image in album.images"
      :key="image.key"
    >
      <v-sheet
       
        height="100%"
        tile
      >
        <v-row
          class="fill-height"
          align="center"
          justify="center"
        >
          <div class="display-3">
           <v-img
      v-bind:src=image alt="Artist Picture" 
    ></v-img>
          </div>
        </v-row>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>


    
      </v-card>
    </v-card>
      
      </v-col>
    </v-row>
    <v-row
          class="fill-height"
          align="center"
          justify="center"
        >
        
             <h3>
        <strong>You might also like: </strong>
             </h3>
            
          <div
            v-for="rec in this.recommendations"
            :key="rec.key"
           
          ><v-col
        cols="12"
        sm="12"
      >
            <AlbumInfo id="rec.id" />
            <v-col
        cols="12"
        sm="12"
      >
          </div>
          
        

    </v-row>
    
</v-container>
</div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import axios from 'axios';
import AlbumInfo from '@/components/AlbumInfo.vue'
@Component
export default class Details extends Vue {
  album: any;

  baseUrl = 'https://api.discogs.com/artists/';
  my_key = '?key=FMvTlSGADQWmohiXndNO&secret=zaYzcFPxvIEZaQJeXpwhJDdPlHQYNTaR';
  recommendations:any;


 getList(album_l:any){
    let list: any[]=[];
    album_l.forEach((element: any) => {
      if(element.id!== this.album.album_id){
     list.push(element);
      }
    });

       return list;
  }

  created() {
      console.log(this.$route.query);
    this.album = {
      album_id: this.$route.query.album_id,
      artist_id: this.$route.query.artist_id,
      title: this.$route.query.title,
      artist: this.$route.query.artist,
      year: this.$route.query.year,
      country: this.$route.query.country,
      images: this.$route.query.images,
      genres: this.$route.query.genres,
      tracklist: this.$route.query.tracklist,
    };
    this.getRecommendations();
    
  }

    async getRecommendations(){
    
    const response =  await axios.get(this.baseUrl + this.album.artist_id +'/releases'+this.my_key);
    const releases = response.data.releases;
    this.recommendations = this.getList(releases);
    console.log(this.recommendations);
  }

 
}
</script>

<style>

</style>