<template>
    <Page>
        <ActionBar :title="beer.name"/>
        <ScrollView orientation="vertical">
            <StackLayout orientation="vertical">
                <img :src="beer.image_url" class="beer-img"/>
                <Label 
                    :text="beer.description" 
                    class="beer-desc"
                    textWrap="true"
                ></Label>
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

    .beer-desc {
        padding: 40px 40px 40px 40px;
        border-top-color: #888;
        border-top-width: 2px;
        color: #888;
    }

    .beer-img {
        margin-top: 60px;
        margin-bottom: 60px;
        width: 200px;
    }
</style>
