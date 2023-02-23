<template>
    <v-container>
        <v-card>
            <v-card-title></v-card-title>
            <v-card-text></v-card-text>
            여기는 메인페이지입니다.
            <v-btn
            variant="flat"
            color="primary"
            @click="testAjax"
            >api 서버통신</v-btn>
            {{ user.id }} {{ user.password }}
        </v-card>
    </v-container>
    123123
</template>

<script setup>
    const { data: posts, refresh } = useLazyAsyncData('posts', () => $fetch('http://localhost:8081/login'));
    const user = ref({ id: '기본', password: '1234'});
    
    const message = 'test123';

    function testAjax() {
        console.log(posts.value);
        user.value.id = posts.value.data.id;
        user.value.password = posts.value.data.password;
    }

</script>
