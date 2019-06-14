<template>
    <Page>
      <ActionBar title="Beer Collection"/>
      <beer-list></beer-list>
    </Page>
</template>

<script>
  import BeerList from './BeerList'

  export default {
    components: { BeerList },
    data() {
      return {
        
      }
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #674172;
        color: #fff;
    }
</style>
