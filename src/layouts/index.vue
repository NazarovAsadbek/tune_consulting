<template>
  <v-app-bar
      app
      color="white"
      dark
  >
        <v-img
            alt="Vuetify Logo"
            contain
            class="shrink"
            width="100"
            src="../../public/img/tune_logo.png"
        />
      <v-spacer></v-spacer>
    <language-switcher />
  </v-app-bar>
</template>

<script>
import languageSwitcher from "@/components/languageSwitcher";
export default {
name: "index",
  components: {languageSwitcher},
  data: () => ({

  }),
}
</script>

<style scoped>
.languageSelect {
  width: 50px;
}
</style>
