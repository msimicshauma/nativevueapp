<template>
    <Page>
        <ActionBar :title="beer.name"/>
        <ScrollView orientation="vertical">
            <StackLayout orientation="vertical">
                <img :src="beer.image_url" class="beer-img"/>
                <StackLayout>
                    <Label text="Description" class="title"></Label>
                    <Label 
                        :text="beer.description" 
                        class="beer-desc"
                        textWrap="true"
                    ></Label>
                </StackLayout>
                <StackLayout>
                    <Label text="Food Pairing" class="title"></Label>
                    <Label 
                        :text="beer.food_pairing" 
                        class="beer-desc"
                        textWrap="true"
                    ></Label>
                </StackLayout>
                <StackLayout>
                    <Label text="Brewers tips" class="title"></Label>
                    <Label 
                        :text="beer.brewers_tips" 
                        class="beer-desc"
                        textWrap="true"
                    ></Label>
                </StackLayout>
            </StackLayout>
        </ScrollView>
    </Page>
</template>

<script>
  export default {
    props: {
        beer: {
            type: Object,
            required: true
        }
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #674172;
        color: #fff;
    }

    .beer-img {
        margin-top: 60px;
        margin-bottom: 60px;
        width: 200px;
    }

    .title {
        margin-left: 40px;
        font-weight: bold;
        color: #674172;
    }

    .beer-desc {
        padding: 40px 40px 40px 40px;
        border-top-color: #674172;
        border-top-width: 2px;
        color: #888;
        font-size: 15px;
    }
</style>
