<template>
    <v-app>
      <NavigationBar/>
      <v-main><slot></slot></v-main>
      <v-footer class="d-flex flex-column p-0" app>
        <div class="px-4 py-2 bg-black text-center w-100">
          {{ new Date().getFullYear() }} — <strong>Study</strong>
        </div>
      </v-footer>
    </v-app>
</template>   