<!-- 1.可以輸入文字的輸入框
2.可以標記的checkbox
3.可以刪除的button
4.可以儲存的button
-->
<script>
export default {
    data() {
        return {
            addText: '',
            toDoListArr: [
                {
                    id: 1,
                    todo: '不要下雨',
                    checkThis: false,
                },
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
        addList() {
            const { addText, toDoListArr } = this;
            if (!addText) return;
            // session清空
            // sessionStorage.removeItem('toDoList');
            // 抓去array裡面的id最大數+1當作是下一個array的id 如果沒有的話則 id 給他1
            const listId = toDoListArr.length ? Math.max(...toDoListArr.map(item => item.id)) + 1 : 1;
            toDoListArr.push({
                id: listId,
                toDo: addText,
                checkThis: false,
            });
            addText = '';
            // 將新的資料存入SESSION，將資料轉成json格式儲存至SESSION內
            sessionStorage.setItem('toDoList', JSON.stringify(toDoListArr));
            // 將新的資料存入localStorage，將資料轉成json格式儲存至localStorage內
            localStorage.setItem('toDoList', JSON.stringify(toDoListArr));
        },

    }
};
</script>

<template>
    <!-- 在使用漸層色的時候，要注意色調要有連續性 -->
    <div class="w-full h-[100vh] bg-slate-500 text-[white] text-center">
        <p class="text-[32px]">ToDoList</p>
        <input type="text" class="w-[300px] border-[2px] mb-[20px] border-[skyblue]">
        <div class="mb-[10px]"><font-awesome-icon :icon="['fas', 'house']" />
            <input type="checkbox">輸入內容
        </div>
        <button type="button" class="border-[1px] me-2" @click="addList()"> 儲存</button>
        <button type="button" class="border-[1px]">刪除</button>
    </div>
</template>



<style scoped="scss"></style>