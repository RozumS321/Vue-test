<template>

  <div id="app">
    <Filters 
    :changeApi='changeApi'
    />
    
    <Photos v-if='checkNasa' v-bind:nasaPhotos="nasaPhotos"/>
    <Photos v-else-if='checkUnsplash' v-bind:unsplashPhotos="unsplashPhotos" />
    <Paginations
      v-if='checkNasa'
      @page-changed='fetchNasaPhoto'
      v-bind:current='currentPage'
      :total='totalPhotos'
      :perPage='perPage'
      />

      <Paginations
      v-else-if='checkUnsplash'
      @page-changed='fetchUnplashPhoto'
      v-bind:current='currentPage'
      :total='totalPhotos'
      :perPage='perPage'
      />

  </div>

</template>


<script>

import Photos from "@/components/photos/Photos";
import Filters from "@/components/filters/Filters";
import Paginations from '@/components/paginations/Paginations'
import axios from "axios";


export default {
  name: 'App',
  components: {
    Photos,
    Filters,
    Paginations,
  },
data() {
    return {
      dataPage: '',
      nasaPhotos: [],
      nasaApi: 'https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&api_key=Y6DTKD0ev9b0aQwT9VIRTeG34ZS83DSjxtSngBoH',
      unsplashApi: `https://api.unsplash.com/photos/?client_id=lDLmvIeW_aq226BAgGN6tUg872-tDblV0asNqz3ZpuQ`,
      unsplashPhotos: [],
      totalPhotos: 0,
      perPage: 24,
      currentPage:1,
      checkNasa: true,
      checkUnsplash: false
    };
  },
  methods: {

   async fetchNasaPhoto(page) {
      await axios(this.nasaApi,{
          params:{
           page: page
          }
        }).then((response) => {
          this.nasaPhotos = response.data.photos;
          this.currentPage = page
          console.log(response)
        });
      },

   async fetchUnplashPhoto(page){
         await axios(this.unsplashApi,{
            params:{
              per_page: this.perPage,
              page: page
            }
          }).then((response) => {
              this.unsplashPhotos = response.data;
              this.totalPhotos = +(response.headers['x-total']);
              this.currentPage = page
          });
    },
    changeApi(type){
        if(type === 'nasa'){
        console.log(type)
        this.checkUnsplash = false,
        this.checkNasa = true,
        this.unsplashPhotos = [],
        this.totalPhotos = 1,
        this.perPage = 24,
        this.currentPage = 1,
        this.fetchNasaPhoto(this.currentPage)
        }
        else if(type === 'unsplash'){
        console.log(type)
        this.checkNasa = false
        this.checkUnsplash = true,
        this.unsplashPhotos = [],
        this.totalPhotos = 1,
        this.perPage = 24,
        this.currentPage = 1,
        this.fetchUnplashPhoto(this.currentPage)
        }
        else{
        this.checkNasa = true
        this.fetchUnplashPhoto(this.currentPage)
        }
    }
  },
  beforeMount() {

  },       
  updated() {

  },

}
</script>

<style >

  body {
    margin: 0;
    padding: 0;
  }

</style>

