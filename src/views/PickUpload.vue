<script>
export default {
    data() {
        return {
            picFile: '',
            fileSrc: '',
            imageFile: [],
        }
    },
    methods: {
        uploadPic(event) {
            this.picFile = event.target.files[0];
            console.log(this.picFile);
            if (this.picFile) {
                const reader = new FileReader();
                reader.readAsDataURL(this.picFile);
                reader.onload = (e) => {
                    console.log(e);
                    this.fileSrc = e.target.result;
                    this.imageFile = [
                        {
                            name: this.picFile.name,
                            path: this.fileSrc,
                        }
                    ];
                    console.log(this.imageFile);
                }
            }
        },
        submit() {
this.imageFile
        }
    },
};
</script>
<template lang="">
<input type="file" accept=".jpg,.png,.jepg,.gif" @change="uploadPic">
<img :src="fileSrc" alt="">
<button class="w-[80px] h-[30px] border border-red-500" type="button" @click="submit()">上傳圖片</button>

</template>
<style lang="scss"></style>