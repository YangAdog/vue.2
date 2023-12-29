<script>
import MyButton from '@/components/customButton/MyButton.vue';

export default{
    components 
    data(){
        return{
            numA:0,
            numB:0,
            result:0,
        }
    },
    methods: {
       
    },
}
</script>
<template>
    <!-- v-if -->
    <!-- v-else-if -->
    <!-- v-else -->

<!-- v-model -->
<div>計算機</div>
<div><label>數字A: <input v-model="numA" type="number"></label></div>
<div><label>數字B: <input v-model="numB" type="number"></label></div>
<div class="btns">
    <button type="button" class="btn">+</button>
    <button type="button" class="btn">-</button>
    <button type="button" class="btn">*</button>
    <button type="button" class="btn">/</button>
</div>
<div class="output text-main-deep">
    計算結果:{{ result }}
</div>
<div class="box text-red-500">
    測試顏色
</div>
</template>

<!-- scoped:目的是為了不要影響到其他區塊的style -->
<style lang="scss" scoped>
.btns {
    @apply flex gap-[30px];

    .btn {
    @apply border-[black] border-[3px] py-[10px] hover:text-[blue] bg-main-deep;
    }
}
.box {
    @apply w-[300px] h-[300px] bg-[wheat] sm:w-[100px] sm:h-[100px];
}
</style>