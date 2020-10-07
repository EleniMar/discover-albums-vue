<template>
 <div class="card"   >
    <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="374"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

        <v-img
      v-bind:src="getImgSource()" alt="Artist Picture" 
    ></v-img>

    <v-card-title>{{title}}</v-card-title>

    <v-card-text>
      <p class="display-1 text--primary">
        <strong>Artist: </strong>
        {{album.artists[0].name}}
      </p>

      <div><p><strong>Year: </strong>{{year}}</p></div>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-actions>
      <v-btn
        color="deep-purple lighten-2"
        text
        @click="viewDetails(album)"
      >
        Details
      </v-btn>
    </v-card-actions>
  </v-card>
 </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';
import axios from 'axios';
@Component
export default class AlbumInfo extends Vue {
    @Prop({required: true}) readonly id: number|undefined
    @Prop(String)  title: string|undefined
    @Prop(String)  artist_name: string|undefined
    @Prop({ default: 0 })
  private _year: number|undefined;
  public get year(): number|undefined {
    return this._year;
  }
  public set year(value: number|undefined) {
    this._year=value;
  }
 
    created() {
    this.getAlbum(this.id);
    
    
  }

  baseUrl = 'https://api.discogs.com/releases/';
  my_key = '?key=FMvTlSGADQWmohiXndNO&secret=zaYzcFPxvIEZaQJeXpwhJDdPlHQYNTaR';
  query = '';
  img_src = '';
  
  
  tracklist:any;
  imageList:any;

  
  album:any;
  
   async getAlbum(id: any){
    let message="";
    let response:any;
    while(true){
      
      response = await axios.get(this.baseUrl + id +this.my_key);
      console.log(response);
      if(response.data!=null){
        
        break;
      }
      
    }
    
    
    this.album=(response.data);
   this.album=this.album;
    this.img_src = this.album.images[0].resource_url;
    this.year = this.album.year;
    
    this.title = this.album.title;
    this.tracklist = this.getTrackList(this.album.tracklist);
    this.imageList = this.getImgList(this.album.images);
    this.$emit( 'sendYear',[this.id,this.year]);
     
  }

  getTrackList(album_l:any){
    let list: any[]=[];
    album_l.forEach((element: any) => {
     list.push(element.title)
    });

       return list;
  }


  

  getImgList(album_l:any){
    let list: any[]=[];
    album_l.forEach((element: any) => {
     list.push(element.resource_url)
    });
      return list;
  }
 
  getImgSource(){
        return this.img_src;
    }

    viewDetails(album: any) {
    this.$router.push({ path: 'details', query: {
      album_id: album.id,
      artist_id: album.artists[0].id,
      title: album.title,
      artist: album.artists[0].name,
      year: album.year,
      country: album.country,
      images: this.imageList,
      genres: album.genres[0],
      tracklist: this.tracklist,
    }});
  }

 
}
</script>