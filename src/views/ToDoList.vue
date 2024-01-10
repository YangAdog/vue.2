<!-- 1.可以輸入文字的輸入框
2.可以標記的checkbox
3.可以刪除的button
4.可以儲存的button
-->

<script>
import Swal from 'sweetalert2'

// // or via CommonJS
// const Swal = require('sweetalert2')

export default {
    data() {
        return {
            addText: '',
            endTime: '',
            toDoListArr: [
                {
                    id: 1,
                    toDo: '第一筆',
                    checkThis: false,
                    // 編輯開關
                    editIng: false,
                    logTime: '2023-12-31',
                    endTime: '2024-02-02',
                    // 編輯文字
                    newToDo: '',
                }
            ],
        };
    },

    // 當網頁載入時會觸發
    mounted() {
        // 將sessionStorage的資料放入toDoListArr內 因為有轉成JSON格式所以要再轉回來
        if (sessionStorage.getItem('toDoList')) {
            this.toDoListArr = JSON.parse(sessionStorage.getItem('toDoList'));
        }
    },

    methods: {
        // 新增功能
        addList() {
            Swal.fire({
                title: "是否要新增ㄅㄅㄐ?",
                icon: "quection",
                showCancelButton: true,
                confirmButtonColor: "#3085d6",
                confirmButtonText: "ㄅㄅㄐ",
                cancelButtonColor: "#d33",
                cancelButtonText: "ㄅㄅ草",
                width: 600,
                padding: "3em",
                color: "#716add",
                background: "#fff url(https://sweetalert2.github.io/images/trees.png)",
                backdrop: `
                rgba(0,0,123,0.4)
                url("https://sweetalert2.github.io/images/nyan-cat.gif")
                left top
                no-repeat
                `
            }).then((result) => {
                if (result.isConfirmed) {

                    // 拿去當下時間
                    let date = new Date().toISOString().split('T');
                    const { addText, toDoListArr, endTime } = this;
                    // 檢測是否為空字串
                    if (!addText || !endTime) return Swal.fire({
                        title: "不要交白卷!",
                        icon: "error",
                        width: 600,
                        padding: "3em",
                        color: "#716add",
                        background: "#fff url(https://sweetalert2.github.io/images/trees.png)",
                        backdrop: `
                        rgba(0,0,123,0.4)
                        url("https://sweetalert2.github.io/images/nyan-cat.gif")
                        left top
                        no-repeat
                        `
                    });

                    // session清空
                    // sessionStorage.removeItem('toDoList');
                    // 抓去array裡面的id最大數+1當作是下一個array的id 如果沒有的話則 id 給他1
                    const listId = toDoListArr.length ? Math.max(...toDoListArr.map(item => item.id)) + 1 : 1;
                    toDoListArr.push({
                        id: listId,
                        toDo: addText,
                        checkThis: false,
                        // 編輯開關
                        editIng: false,
                        logTime: date[0],
                        endTime: endTime,
                        // 編輯的文字
                        newToDo: '',
                    });
                    this.addText = '';
                    this.endTime = '';
                    // 將新的資料存入SESSION，將資料轉成json格式儲存至SESSION內
                    sessionStorage.setItem('toDoList', JSON.stringify(toDoListArr));
                    // 將新的資料存入localStorage，將資料轉成json格式儲存至localStorage內
                    // localStorage.setItem('toDoList', JSON.stringify(toDoListArr));
                    Swal.fire({
                        title: "ㄅㄅㄐ!",
                        icon: "success",
                        width: 600,
                        padding: "3em",
                        color: "#716add",
                        background: "#fff url(https://sweetalert2.github.io/images/trees.png)",
                        backdrop: `
                        rgba(0,0,123,0.4)
                        url("https://sweetalert2.github.io/images/nyan-cat.gif")
                        left top
                        no-repeat
                        `
                    });
                }
            });

        },
        editList(id) {
            console.log(id);

        },
        // 刪除功能
        deleteList(id) {
            const { toDoListArr } = this;
            // 找尋跟id不一樣的留下來
            const deleteList = toDoListArr.filter(item => item.id !== id);
            // 如果要修改data的值，還是要加上this.
            this.toDoListArr = deleteList;
            // 再放進localStorage內就可以完成刪除
            // localStorage.setItem('toDoList', JSON.stringify(deleteList));
            // console.log(deleteList);
            sessionStorage.setItem('toDoList', JSON.stringify(deleteList));
            console.log(deleteList);
        },

        // 修改觸發
        starEdit(item) {
            // 編輯開關打開
            item.editIng = !item.editIng;
            // 舊的事項放入newToDo
            item.toDo = item.newToDo;
        },

        topEditst(item) {
            item.editIng = !item.editIng;
            item.toDo = item.newToDo;
            item.newToDo = '';
        },
    }
};
</script>

<template>
    <!-- 在使用漸層色的時候，要注意色調要有連續性 -->
    <div
        class="w-full h-[100vh] bg-gradient-to-b from-indigo-500 via-purple-500 to-pink-500 flex items-center justify-center font-big">
        <!-- 進度條位置 1.要跟現在的事項數量一致 2.只要勾起來就計算為完成進度條就會填上進度 -->
        <div class="w-[70%] bg-white rounded-md">
            <div class="flex items-center justify-center border-b-2 gap-5">
                <input v-model="addText" type="text" class="w-full h-10 ml-3 border-2" placeholder="請填寫事項">
                <button
                    class="bg-gradient-to-b from-indigo-500 via-purple-500 to-pink-500 p-3 rounded-xl m-3 text-white text-xl"
                    type="button" @click="addList()"><font-awesome-icon :icon="['fas', 'file-import']" /></button>
            </div>
            <div class=" border-[1px] text-center border-[skyblue]">
                <div>
                    紀錄時間 <input type="date" name="" id="">
                </div>
                <div>
                    期限 <input v-model="endTime" type="date" name="" id="">
                </div>
            </div>
            <div class="w-full grid grid-cols-5 gap-4">
                <div>執行</div>
                <div class="grid grid-cols-subgrid ">事項</div>
                <div>期限</div>
                <div>紀錄時間</div>
                <div class="text-center">刪除</div>
            </div>
            <div class="overflow-y-scroll h-[500px]">
                <div v-for=" item in toDoListArr" :key="item.id" class="flex items-center justify-between gap-5 border-b-2"
                    :class="{ 'bg-neutral-950 text-white line-through': item.checkThis === true }">
                    <div class="w-full grid grid-cols-5 items-center">
                        <div>
                            <!-- 執行結束，勾選起來後 要把刪除按鈕拿掉 -->
                            <input v-model="item.checkThis" class="ml-3" type="checkbox" @change="">
                        </div>
                        <span v-if="!item.editIng" class="grid grid-cols-subgrid" @click="starEdit(item)">{{ item.toDo }}</span>
                        <span>{{ item.endTime ?? '' }}</span>
                        <span>{{ item.logTime }}</span>
                        <button class="bg-gradient-to-b from-red-500  to-orange-500 p-3 rounded-xl m-3 text-white"
                            type="button" @click="deleteList(item.id)"><font-awesome-icon
                                :icon="['fas', 'trash-can']" /></button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- <div class="w-full h-[100vh] bg-slate-500 text-[white] text-center">
        <p class="text-[32px]"><font-awesome-icon :icon="['fas', 'house']" />ToDoList</p>
        <input type="text" class="w-[300px] border-[2px] mb-[20px] border-[skyblue]">
        <div class="mb-[10px]">
            <input type="checkbox">輸入內容
        </div>
        <button type="button" class="border-[1px] me-2" @click="addList()"> 儲存</button>
        <button type="button" class="border-[1px]">刪除</button>
    </div> -->
</template>



<style lang="scss" scoped></style>