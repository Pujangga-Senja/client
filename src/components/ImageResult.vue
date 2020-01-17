<template>
    <div class="container">
        <b-img-lazy v-bind="mainProps" v-bind:src="imageUrl" fluid alt="Responsive image"></b-img-lazy>
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
            }
        }
    },
    props: ['imageUrl']
}
</script>

<style lang="css" scoped>
    
</style>