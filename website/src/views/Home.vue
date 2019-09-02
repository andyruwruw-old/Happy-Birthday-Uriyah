<template>
  <div class="home">
    <Fireman type="type"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Fireman from '@/components/Fireman.vue'

export default {
  name: 'home',
  components: {
    Fireman
  }
}
</script>
