<template>
<form>
    <div class='filters'>
        <input placeholder="search name" type='text'/>

        <div class="filters-radio">

            <div class='filters-radio-input'>
                <input type="radio" id="nasa" name="api" checked>
                <label for="nasa">Nasa API</label>
            </div>

            <div class='filters-radio-input'>
                <input type="radio" id="other" name="api">
                <label for="other">Other API</label>
            </div>

        </div>
    </div>
</form>
</template>

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