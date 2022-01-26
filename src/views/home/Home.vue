<template>
  <div class="page">
    <div class="container-fluid p-4">
      <h2>Home</h2>
      <hr>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'Home',

  computed: {
    ...mapState('auth', ['user'])
  }
}
</script>
