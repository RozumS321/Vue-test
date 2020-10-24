<template>
    <div class='photos'>
        <Photo 
            v-for="data of dataPage" 
            v-bind:key="data.id"
            v-bind:data = "data"
        />

    </div>
</template>

<script>

import Photo from "@/components/photo/Photo"


export default {
    props:['dataPage'],
    components:{
    Photo
    }
}

</script>

<style scoped>

    .photos{
display: grid;
grid-template-columns: repeat(4, 1fr);
grid-template-rows: repeat(auto,1fr);
grid-column-gap: 1rem;
grid-row-gap: 1rem;
}

</style>