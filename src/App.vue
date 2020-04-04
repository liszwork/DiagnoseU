<template>
  <v-app :dark="setTheme">
    <v-content>
      <!-- <v-switch label="Dark Theme" v-model="isDark"></v-switch> -->
      <SMScale />
      <!-- <SampleParent /> -->
    </v-content>
  </v-app>
</template>

<script>
import SampleParent from "./components/SampleParent";
import SMScale from "./components/SMScale/SMScale";

export default {
  name: "App",
  components: {
    SampleParent,
    SMScale
  },
  data: () => ({
    isDark: false,
  }),
  computed: {
    setTheme() {
      return this.$vuetify.theme.dark = (this.isDark == true);
    }
  }
};
</script>
