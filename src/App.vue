<template>
  <div id="app">
    <page-list></page-list>
  </div>
</template>

<script>
import pageList from './components/pageList'

export default {
  name: 'App',
  components: {
    pageList
  }
}
</script>

<style>
#app {
  color: #2c3e50;
  margin-top: 60px;
}
</style>
