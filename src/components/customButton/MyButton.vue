<script>
export default {

}
</script>
<template>
    <section id="myBtn">
        <button type="button" class="btn">
            <slot />
        </button>
        <!-- <div class="btn2">
            <button type="button" class="1">
                <slot />
            </button>
            <button type="button" class="2">
                <slot />
            </button>
            <button type="button" class="3">
                <slot />
            </button>
            <button type="button" class="4">
                <slot />
            </button>
            <button type="button" class="5">
                <slot />
            </button>
            <button type="button" class="6">
                <slot />
            </button>
            <button type="button" class="7">
                <slot />
            </button>
            <button type="button" class="8">
                <slot />
            </button>
            <button type="button" class="9">
                <slot />
            </button>
            <button type="button" class="0">
            <slot />
        </button>
    </div> -->
</section>
</template>
    
    
<style lang="scss" scoped>#myBtn {
    .btn {
        @apply w-[50px] border-[black] border-[1px] py-[10px] mb-[50px] hover:text-[blue] bg-main-deep;
    }

    .btn2 {
        @apply border-[blue] border-[1px] w-[20px] h-[30px] bg-slate-500;
    }
}</style>