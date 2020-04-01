<template>
  <v-app>
    <v-content>
      <SampleParent />
    </v-content>
  </v-app>
</template>

<script>
import SampleParent from "./components/SampleParent";

export default {
  name: "App",

  components: {
    SampleParent,
    // Sample,
    // SampleResult
  },

  data: () => ({
    //
  })
};
</script>
