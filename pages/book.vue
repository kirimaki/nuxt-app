<template>
    <v-container class="todo-section">
        <v-card v-for="todo in todos" :key="todo">
            <v-card-title>{{ todo.title }}</v-card-title>
            <v-card-text>{{ todo.content }}</v-card-text>
        </v-card>
        <v-card class="mt-5">
            <v-card-text>{{ count }}</v-card-text>
            <v-card-text>{{ count2 }}</v-card-text>
            <v-btn color="secondary" @click="countAdd">숫자를 1 증가</v-btn>
        </v-card>
    </v-container>
    <!-- <component :is="true ? join : todo" /> -->
    <h1 v-my:test="{'test':1234, 'test2':5678}">this is a heading</h1>
    <div v-color="`blue`">이건 v-color의 바인딩 value를 따른다</div>
    <join v-color="`red`" :test2="count" @change="change"></join>
</template>

<script setup>
import data from "~~/assets/javascripts/data";
import join from './join.vue';
import todo from './todo.vue';

const todos = ref([...data]);
let count = ref(0);
let count2 = ref(0);
let count3 = ref(0);
function countAdd() {
    count.value++;
    count2.value++;
    count3.value++;
}

const vMy = {
    beforeMount: (el, test) => {
        console.log(el);
    },
}

const vColor = {
    beforeMount: (el, binding, vnode, prevNode) => {
        console.log(el);
        el.style.color = binding.value;
        
    },
}

function change(val) {
    if(val === 'add') {
        count.value++;
    } else {
        count.value--;
    }
    console.log(val);
}

</script>


<style lang="scss">
.todo-section {
    width: 600px;
}
</style>