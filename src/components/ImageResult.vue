<template>
    <div class="container">
        <div class="share">
            <a class="twitter-share-button"
            v-bind:href="url" data-size="large">
            Tweet
            </a>
        </div>
        <div class="image">
            <b-img-lazy v-bind="mainProps" v-bind:src="imageUrl" fluid alt="Responsive image"></b-img-lazy>
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
    a[href*="twitter.com/"] {
  background:url(https://twitter.com/favicon.ico) no-repeat left center;
  padding-left:19px;
  padding: 3px;
  background-color: rgb(45, 114, 241);
  color: white;
  font-weight: 500;
  border-radius: 7px;
  width: 5vw;
  text-align: right;
  margin: 3px;
  text-decoration: none
}
</style>