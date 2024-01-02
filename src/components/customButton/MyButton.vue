<script>
export default{

}
</script>
<template>
<section id="myBtn">
    <button type="button" class="btn">
        <slot/>
    </button>
</section>
</template>
    
    
<style lang="scss" scoped>
    #myBtn{
        .btn {
    @apply border-[black] border-[3px] py-[10px] hover:text-[blue] bg-main-deep;
    }
    }
</style>