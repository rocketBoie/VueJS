<template>
    <div class="w-full  text-center mt-4 flex justify-center items-center flex-col gap-10 px-4">
        <h1 class="text-4xl font-bold text-blue-700">{{ msg }}</h1>

        <div class="flex w-full max-w-md">
            <input v-model="inputText" type="text" required placeholder="Add a new task..."
                class="flex-1 px-4 py-2 border border-gray-300 rounded-l-md focus:outline-none focus:ring-2 focus:ring-blue-500" />
            <button @click="addList"
                class="bg-blue-500 text-white px-4 py-2 rounded-r-md hover:bg-blue-600 transition">Add</button>
        </div>

        <div v-for="(ar, index) in arr" :key="index"
            class="bg-white shadow p-3 rounded flex justify-between items-center gap-10 w-100">
            <div><span>{{ ar.text }}</span></div>
            <div class="flex gap-2">
                <button class="bg-red-500 text-white px-2 py-1 rounded hover:bg-red-600"
                    @click="deleteListItem(index)">Delete </button>
                <button class="bg-yellow-400 text-white px-2 py-1 rounded hover:bg-yellow-500"
                    @click="editListItem(index)">Edit</button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";
const msg = ref("Welcome To TodoList");
const inputText = ref('')
const arr = ref([])
const isEditing = ref(false)
const isEditingIndex = ref(-1)
const nextId = ref(1)

function addList() {
    if (inputText.value.trim().length > 0) {
        if (isEditing.value) {
            arr.value[isEditingIndex.value].text = inputText.value.trim();
            isEditing.value = false;
            isEditingIndex.value = -1
        } else {
            arr.value.push({ id: nextId.value++, text: inputText.value.trim() });
        }
        inputText.value= '';
    } else {
        alert("Add items 😒😒😒😒");
    } 
}

function deleteListItem(index){
    arr.value.splice(index, 1)
}

function editListItem(index){
    inputText.value = arr.value[index].text
    isEditing.value = true
    isEditingIndex.value = index
}
</script>

<!-- <script>
export default {
    data() {
        return {
            msg: "Welcome To TodoList",
            i    nputText: '',
            arr: [],
            nextId: 1,
            isEditing: false,
            isEditingIndex: -1
        }
    },
    methods: {
        addList() {
            if (this.inputText.trim().length > 0) {
                if (this.isEditing) {
                    this.arr[this.isEditingIndex].text = this.inputText.trim();
                    this.isEditing = false;
                    this.isEditingIndex = -1
                } else {
                    this.arr.push({ id: this.nextId++, text: this.inputText.trim() });
                }
                this.inputText = '';
            } else {
                alert("Add items 😒😒😒😒");
            }
        },
        deleteListItem(index) {
            this.arr.splice(index, 1)
        },
        editListItem(index) {
            this.inputText = this.arr[index].text
            this.isEditing = true
            this.isEditingIndex = index
        }
    }
}
</script> -->
