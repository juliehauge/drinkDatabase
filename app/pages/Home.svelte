<script>
    import Gin from './Gin.svelte'

    let searchPhrase = ''
    
    const searchedDrink = (evt) => {
        const {value} = this.elements.search
        searchPhrase = value
    }
</script>

<frame>
<page>
    <stackLayout>
    <searchBar 
        hint='what drink would you like to make?' 
        bind:text='{searchPhrase}' 
        on:submit|preventDefault='{searchedDrink}'
        />
        <image 
            class='img' 
            src='https://dbdzm869oupei.cloudfront.net/img/sticker/preview/20007.png' 
            alt='cover' 
            stretch='aspectFill' 
            />
    </stackLayout>
</page>
</frame>

<style>
    .img{
        margin-top: 12;
        margin-bottom: 12;
        height: 75%;
    }
</style>