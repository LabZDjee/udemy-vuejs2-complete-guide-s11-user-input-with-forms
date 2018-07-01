<template>
 <div>
    <div class="form-group">
        <label for="ncv1">Given Name: </label>
        <input id="ncv1" type="text" v-model="value.givenName">
<!--    which is equivalent to:
        <input id="ncv1" type="text" :value="value.givenName" @input="value.givenName=$event.target.value">
 -->    
    </div>
    <div class="form-group">
        <label for="ncv2">Family Name: </label>
        <input id="ncv2" type="text" :value="value.familyName" @input="value.familyName=$event.target.value">
    </div>
 </div>   
</template>

<script>
    export default {
     props: ["value"]
    }
</script>

<style scoped>
</style>
