<template>
    <div class="container">
        <div class="image">
            <b-img-lazy v-bind="mainProps" v-bind:src="imageUrl" fluid alt="Responsive image"></b-img-lazy>
        </div>
        <div class="share">
            <a class="twitter-share-button"
            v-bind:href="url" data-size="large">
            Tweet
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name: "ImageResult",
    data(){
        return {
            mainProps: {
                center: true,
                fluidGrow: true,
                blank: true,
                blankColor: '#bbb',
                width: 500,
                height: 300,
                class: 'my-5'
            },
            url: 'https://twitter.com/intent/tweet?text=Here is your Images!'+this.imageUrl
        }
    },
    props: ['imageUrl']
}
</script>

<style lang="css" scoped>
    
</style>