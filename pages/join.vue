<template>
    <v-container>
        <v-card>
            <v-card-title>회원가입</v-card-title>
            <v-card-item>
                <v-form ref="form" @submit.prevent>
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
                            {{ props.test2 }}
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
                            <v-btn @click="test" type="submit" color="primary" block>회원가입</v-btn>
                        </v-col>
                        <v-col cols="6">
                            <v-btn color="warning" to="/" block>취소</v-btn>
                        </v-col>
                        <v-col cols="6">
                            <v-btn @click="addCount" block>더하기</v-btn>
                            <v-btn @click="minusCount" block>빼기</v-btn>
                        </v-col>
                    </v-row>
                </v-form>
            </v-card-item>
        </v-card>
    </v-container>
</template>

<script setup>
    console.log(props);
    const props = defineProps({
        test2: {
            type: Number,
            required: true,
            default: 0,
            validator(value) {
                return true;
            }
        },
        count: Number,
    })

    const emit = defineEmits(['change']);

    function addCount() {
        emit('change', 'add');
    }

    function minusCount() {
        emit('change', 'minus');
    }

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

    function test() {
        const data2 = {
            idInput : idInput.value,
            passInput : passInput.value
        }
        console.log(data2);
        const { data: posts, refresh } = useLazyAsyncData('posts', () => $fetch('http://localhost:8081/join', {
            headers: {
                //"Content-Type": "multipart/form-data",
            },
            method: 'POST',
            body: data2
        }));
        console.log(posts.value);
    }

</script>