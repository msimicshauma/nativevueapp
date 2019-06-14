<template>
    <ListView for="beer in beers">
        <v-template>
            <StackLayout @tap="$navigateTo(BeerInfo)" class="beerItem">
                <Label :text="beer.name"></Label>
                <Label :text="beer.tagline"></Label>
            </StackLayout>
        </v-template>
   </ListView>
</template>

<script>
  import BeerInfo from './BeerInfo'
  export default {
    data() {
      return {
        beers: null
      }
    },
    created() {
      fetch('https://api.punkapi.com/v2/beers')
      .then(res => {
        return res.json()
      })
      .then(beerData => {
        this.beers = beerData
      })
    }
  }
</script>

<style scoped>
    .beerItem {
      text-align: left;
      padding: 20px 20px 20px 20px;
      border-bottom-color: #888;
      border-bottom-width: 2px;
      color: #888;
    }
</style>
