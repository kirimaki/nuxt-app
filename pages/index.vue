<template>
    <v-container>
        <v-card>
            <v-card-title></v-card-title>
            <v-card-text></v-card-text>
            여기는 메인페이지입니다.
        </v-card>
        <v-btn
        variant="flat"
        color="primary"
        @click="testAjax"
        >api 서버통신</v-btn>
        <v-btn @click="contactForm">이거는 즉각 api 통신</v-btn>
        {{ user.id }} {{ user.password }}
    </v-container>
</template>

<script setup>
    const user = ref({ id: '기본', password: '1234'});
    const { data: posts, refresh } = await useLazyAsyncData('posts', () => $fetch('http://localhost:8081/login'));
    
    const message = 'test123';
    console.log(posts.value);
    console.log("test");

    function testAjax() {
        console.log(posts.value);
        user.value.id = posts.value.data.id; 
        user.value.password = posts.value.data.password;
    }

    function contactForm() {
        const data = $fetch('http://localhost:8081/login', {
            method: 'GET',
        });
        data.then((val) => {
            console.log(val.data.id);
            user.value.id = val.data.id;
            user.value.password = val.data.password;
        }) 
    }

</script>
