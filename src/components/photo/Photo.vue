<template>
    <div class="photo">

        <div class='data-img'>
            <img alt="s" :src='data.img_src'/>
        </div>

        <div class="data-info" >

            <span>{{'id: ' + data.id}}</span> 
            <span>{{'earth-date: ' + data.earth_date}}</span> 
            <span>{{'camera name: ' + data.camera.full_name}}</span> 

        </div>

    </div>
</template>


<script>

export default {
props: {
    data:{
        type:Object,  
        required: true
    },
   }
}


</script>



<style>

.photo{
    border: 2px solid #000;
    display: flex;
    flex-direction: column;
    margin-top: 1rem;
}

.data-info{
    border-top: 2px solid #000;
    color: #000;
    display: flex;
    flex-direction: column;
    font-size: 1.5rem;
}

img {
  height: 20vw;
  width: 100%;
}

</style>