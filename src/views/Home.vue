<template>
  <div class="home">
    <SearchBox/>
  </div>
</template>

<script>
// @ is an alias to /src
import SearchBox from '@/components/SearchBox.vue'

export default {
  name: 'home',
  components: {
    SearchBox
  }
}
</script>
