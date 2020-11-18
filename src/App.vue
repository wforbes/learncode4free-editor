<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <span class="text-h4">Learn Code For Free</span>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/wforbes/learncode4free-parser"
        target="_blank"
        text
      >
        <span class="mr-2">Code on Github</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <Editor/>
    </v-main>
  </v-app>
</template>

<script>
import Editor from '@/components/Editor';

export default {
  name: 'App',

  components: {
    Editor,
  },

  data: () => ({
    //
  }),
};
</script>
