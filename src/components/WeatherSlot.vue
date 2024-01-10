<script>
export default {
data() {
    return {
        thisText:'ㄅㄅㄐ'
    };
},
}
</script>

<template>
 <button type="button" class="p-3 rounded-md bg-red-800">
<slot />
 </button>

</template>
<style lang="scss" scoped>
</style>