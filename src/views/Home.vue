<template>

  <div class="container">
    <Header title='BaharStrap'/>
    <Welcome />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/templates/header'
import Welcome from '@/components/welcome'

export default {
  name: 'Home',
  components: {
    Header,
    Welcome
  }
}
</script>
