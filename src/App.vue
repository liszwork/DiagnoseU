<template>
  <v-app>
    <v-content>
      <Sample/>
    </v-content>
  </v-app>
</template>

<script>
import Sample from './components/Sample'

export default {
  name: 'App',

  components: {
	Sample,
  },

  data: () => ({
    //
  }),
};
</script>
