<script>
import MyButton from '@/components/customButton/MyButton.vue';

export default{
    components : {
        MyButton
    },
    data(){
        return{
            numA:0,
            numB:0,
            result:0,
        }
    },
    methods: {
       add(){
        if(this.numA.toString().trim()===''||this.numB.toString().trim()==='') return;
        this.result=this.numA + this.numB;
       },
       minus(){
        if(this.numA.toString().trim()===''||this.numB.toString().trim()==='') return;
        this.result=this.numA - this.numB;
       },
       mult(){
        if(this.numA.toString().trim()===''||this.numB.toString().trim()==='') return;
        this.result=this.numA * this.numB;
       },
       divi(){
        if(this.numA.toString().trim()===''||this.numB.toString().trim()==='') return;
        this.result=this.numA / this.numB;
       },
    },
}
</script>
<template>
    <!-- v-if -->
    <!-- v-else-if -->
    <!-- v-else -->

    <!-- v-show -->

    <!-- v-for 記得要補:key -->


<!-- v-model -->
<div>計算機</div>
<div><label>數字A: <input v-model="numA" type="number"></label></div>
<div><label>數字B: <input v-model="numB" type="number"></label></div>
<div class="btns">
    <MyButton @click="add()">+</MyButton>
    <MyButton @click="minus()">-</MyButton>
    <MyButton @click="mult()">*</MyButton>
    <MyButton @click="divi()">/</MyButton>

    <!-- <MyButton>-</MyButton>
    <MyButton>*</MyButton>
    <MyButton>/</MyButton> -->

    <!-- <button type="button" class="btn">+</button>
    <button type="button" class="btn">-</button>
    <button type="button" class="btn">*</button>
    <button type="button" class="btn">/</button> -->
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

   
}
.box {
    @apply w-[300px] h-[300px] bg-[wheat] sm:w-[100px] sm:h-[100px];
}
</style>