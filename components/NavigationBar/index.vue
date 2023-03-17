<template>
    <v-app-bar :elevation="4">
        <v-app-bar-nav-icon to="/" />
        <v-app-bar-title>JY</v-app-bar-title>
        <template v-slot:append>
            <v-btn icon="mdi-heart" to="/join"></v-btn>

            <v-btn icon="mdi-magnify" to="/"></v-btn>

            <v-menu location="bottom">
                <template v-slot:activator="{ props }">
                    <v-btn 
                    icon="mdi-dots-vertical" 
                    v-bind="props"
                    >
                    </v-btn>
                </template>
                <v-list>
                    <v-list-item 
                    v-for="item in items" 
                    :key="item" 
                    class="test"
                    :to="item.to"
                    >
                        <template v-slot:prepend>
                            <v-icon :icon=item.icon></v-icon>
                        </template>
                        <v-list-item-title>{{ item.text }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
            
        </template>
</v-app-bar>
</template>

<script setup>
    const items = ref([
        { text: 'Todo', icon: 'mdi-calendar-edit', to: '/todo'},
        { text: '내 정보', icon: 'mdi-account' },
        { text: '로그아웃', icon: 'mdi-logout' },
        { text: '책 리스트', icon: 'mdi-book', to: '/book' },
      ]);
</script>

<style lang="scss">
.test:hover {
    background: #9e9e9e;
    cursor: pointer;
}
</style>