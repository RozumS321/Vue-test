<template>
<form>
    <div class='filters'>

        <div class="filters-radio" >  
        <select v-model="selected" @change="changeApi(selected)">
        <option disabled value="">Selected API</option>
            <option value='nasa'>Nasa API</option>
            <option value='unsplash'>unsplash API</option>
        </select>

        </div>
    </div>
</form>
</template>

<script>
export default {
    props:{
     changeApi:{
         type: Function
     }
    },
    methods:{

    }

}
</script>

<style scoped>

.filters {
    margin-top: 1rem;
    display: flex;
    justify-content: center;
}
.filters-radio{
    display: flex;
    margin-left: 1rem;
}

.filters-radio-input {
    margin-left: 1rem;
    
}

</style>