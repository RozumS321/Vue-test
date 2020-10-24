<template>
  <div id="app">
    <Filters />
    <Photos v-bind:dataPage="dataPage"/>
  </div>
</template>

<script>
import Photos from "@/components/photos/Photos";
import Filters from "@/components/filters/Filters";
import axios from "axios";


export default {
  name: 'App',
  components: {
    Photos,
    Filters
  },
data() {
    return {
      dataPage: '',
      //   labels: [
      //   {label:'s', id:'1', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'w', id:'2', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'q', id:'3', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'q', id:'4', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'q', id:'5', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'q', id:'6', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'q', id:'7', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'q', id:'8', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'q', id:'9', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'q', id:'10', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      //   {label:'q', id:'11', src:'http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486265257EDR_F0481570FHAZ00323M_.JPG' },
      // ],
      marsPhotos: [],
      marsPhotosApiUrl: 'https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&page=20&api_key=Y6DTKD0ev9b0aQwT9VIRTeG34ZS83DSjxtSngBoH',
    };
  },
  methods: {
  getApiData() {
      axios({
        url: this.marsPhotosApiUrl,
        method: 'GET',

      }).then((response) => {
        this.dataPage = response.data.photos;
        console.log(this.dataPage)
      });
    }
  },
  beforeMount() {
    this.getApiData()
  },
  mounted() {
  },

}
</script>

<style >

  body {
    margin: 0;
    padding: 0;
  }

</style>

