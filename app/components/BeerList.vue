<template>
    <PullToRefresh @refresh="refreshList">
        <ListView for="beer in beers" @loadMoreItems="getBeers">
            <v-template>
                <FlexboxLayout 
                    class="beer-item"
                    flexDirection="row"
                    justifyContent="space-between"
                    @tap="loadBeer(beer)"
                > 
                    <StackLayout orientation="vertical">
                        <Label :text="beer.name" textWrap="true" class="beer-name"></Label>
                        <Label :text="beer.tagline" textWrap="true" class="beer-tagline"></Label>
                    </StackLayout>
                    <img :src="beer.image_url" class="beer-img"/>
                </FlexboxLayout>
            </v-template>
        </ListView>
    </PullToRefresh>
</template>

<script>
  import BeerInfo from './BeerInfo'
  import Vue from 'nativescript-vue';
 
  Vue.registerElement(
    'PullToRefresh',
    () => require('nativescript-pulltorefresh').PullToRefresh
  );

  export default {
    data() {
      return {
        beers: [],
        page: 1,
        loadMore: true
      }
    },
    created() {
      this.getBeers()
    },
    methods: {
        refreshList(args) {
            var pullRefresh = args.object;
            this.beers = []
            this.page = 1

            this.getBeers()
            .then(res => {
                setTimeout(() => {
                    pullRefresh.refreshing = false;
                }, 1000);
            })
        },
        getBeers() {
            return new Promise((resolve, reject) => {
                fetch(`https://api.punkapi.com/v2/beers?page=${this.page}&per_page=15`)
                .then(res => {
                    return res.json()
                })
                .then(beersList => {
                    this.beers = this.beers.concat(beersList)
                    this.page++
                    resolve('success')
                })
                .catch(error => {
                    reject(error)
                })
            })
        },
        loadBeer(beer) {
            this.$navigateTo(BeerInfo, { props: { beer } })
        }
    },
  }
</script>

<style scoped>
    .beer-item {
      padding: 40px 40px 40px 40px;
      border-bottom-color: #674172;
      border-bottom-width: 2px;
      color: #888;
    }

    .beer-img {
        width: 30px;
    }

    .beer-name {
        width: 500px;
        font-size: 14px;
        font-weight: bold;
    }

    .beer-tagline {
        width: 500px;
        font-size: 14px;
        margin-top: 10px;
    }
</style>
