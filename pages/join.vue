<template>
    <v-container>
        <v-card>
            <v-card-title>회원가입</v-card-title>
            <v-card-item>
                <v-form ref="form" @submit="test" @submit.prevent>
                    <v-row>
                        <v-col cols="12">
                            <v-text-field
                            type="input"
                            hint="아이디는 10자 이내입니다."
                            label="아이디"
                            :counter="10"
                            :rules="idRules"
                            v-model="idInput"
                            clearable
                            >
                            </v-text-field>
                            <v-text-field
                            type="password"
                            hint="비밀번호는 8~10자입니다."
                            label="비밀번호"
                            :counter="10"
                            :rules="idRules"
                            v-model="passInput"
                            clearable
                            >
                            </v-text-field>
                        </v-col>
                        <v-col cols="6">
                            <v-btn type="submit" color="primary" block>회원가입</v-btn>
                        </v-col>
                        <v-col cols="6">
                            <v-btn color="warning" to="/" block>취소</v-btn>
                        </v-col>
                    </v-row>
                </v-form>
            </v-card-item>
        </v-card>
    </v-container>
</template>

<script setup>
    // export default {
    //     data: () => (
    //         {
    //             idRules: [
    //                 value => {
    //                     if(value) return true;
    //                     return 'id is Required.';
    //                 },
    //                 value => {
    //                     if (value?.length <= 10) return true
    //                     return 'Name must be less than 10 characters.'
    //                 },
    //             ]
    //         }
    //     )
    // }
    const idRules = [
        value => {
            if(value) return true;
            return '아이디 입력 ㄱㄱ';
        },
        value => {
            if(value?.length <= 10) return true
            return '아이디 선 씨게 넘음.';
        }
    ]
    const form = ref(null);
    const idInput = ref(null);
    const passInput = ref(null);

    function test(data) {
        const data = {
            
        }
        console.log(data);
        const { data: posts, refresh } = useLazyAsyncData('posts', () => $fetch('http://localhost:8081/join', {
            method: 'POST',
            body: data
        }));
        console.log(posts.value);
        console.log(idInput.value);
        console.log(passInput.value);
    }

</script>