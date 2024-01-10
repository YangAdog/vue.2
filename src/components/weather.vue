<script>
export default {
 data(){
    return{
        weather: [],
    };
 },
 mounted(){
    fetch('')
    .then(res =>{
        res.json();
    })
    .then(resluts =>{
        console.log(resluts);
        this.weather = resluts;
    })
 },
}
</script>
<template lang="">
    <div>
        
    </div>
</template>
<style lang="">
    
</style>