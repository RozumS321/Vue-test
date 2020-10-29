<template>
<div class="photo">
        <div class='data-img'>
            <img :src="unsplashPhoto.urls.small" alt="">
        </div>
</div>
</template>

<script>


export default {
    props: {
        unsplashPhoto:{
            type: Object,
            required: true
        },
    },

}
</script>

<style scoped>

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