<template>
  <v-app>
    <v-content>
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
    SMScale,
  },

  data: () => ({
    //
  })
};
</script>
