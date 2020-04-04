<template>
  <v-app :dark="setTheme">
    <v-content>
      <v-toolbar color="blue">
        <v-toolbar-title class="display-1 font-weight-black">{{ title }}</v-toolbar-title>
      </v-toolbar>

      <!-- <v-switch label="Dark Theme" v-model="isDark"></v-switch> -->
      <SMScale @update-title="updateTitle" />
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
    title: "自分を知ろう！"
  }),
  methods: {
    updateTitle(title) {
      this.title = title;
    }
  },
  computed: {
    setTheme() {
      return (this.$vuetify.theme.dark = this.isDark == true);
    }
  }
};
</script>
