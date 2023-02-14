<template>
    <v-app theme="">
      <v-app-bar :collapse="false" rounded :elevation="2">
          <v-app-bar-nav-icon />
          <v-app-bar-title>asd</v-app-bar-title>
      </v-app-bar>
      <v-navigation-drawer
        expand-on-hover
        rail
      >
        <v-list>
          <v-list-item
            prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg"
            title="Sandra Adams"
            subtitle="sandra_a88@gmailcom"
          ></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item to="/file" prepend-icon="mdi-folder" title="내 파일" value="내 파일">
          </v-list-item>
          <v-list-item to="/todo" prepend-icon="mdi-account-multiple" title="사용자 리스트" value="사용자">
          </v-list-item>
          <v-list-item prepend-icon="mdi-star" title="즐겨찾기" value="즐겨찾기"></v-list-item>
        </v-list>
      </v-navigation-drawer>

      <v-main>
        <slot />
      </v-main>

      <v-footer app>asd</v-footer>
    </v-app>
</template>