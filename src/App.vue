<template>
  <v-app>
      <index-layout />
    <v-main>
      {{ $t('hello') }}
    </v-main>
  </v-app>
</template>

<script>
import indexLayout from './layouts/index'
export default {
  components: {indexLayout},
  name: 'App',
  data: () => ({}),
  methods: {}
};
</script>
