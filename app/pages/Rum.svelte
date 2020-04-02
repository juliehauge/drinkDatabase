<script>
    import {onMount} from 'svelte'
    import {showModal} from 'svelte-native'
  
    import Drink from '../modals/Drink.svelte' 
  
    let drinkType = 'rum'
    const url = `https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${drinkType}`
    
    let drinks = []


    onMount(() => {
        fetch(url)
            .then(response => response.json())
            .then( json => {
                drinks = json.drinks
            })
            .catch(error => console.log(error))
    })

    const showDrink = async (drink) => {
        await showModal(
            {
                page: Drink,
                props:{
                    drink:drink

                }
            }
        )
    }

    let searchPhrase = ''
    $: searchedDrink = drinks.filter(drink => drink.strDrink.includes(searchPhrase))
</script>

<stackLayout>
    <searchBar 
        hint='what rum cocktail would you like to make?' 
        bind:text='{searchPhrase}' 
        />
    <scrollView>
        <stackLayout class='articles'>
            {#if searchPhrase}
                {#each searchedDrink as search}
                    <stackLayout 
                        borderColor='lightyellow'
                        borderWidth='5'
                        borderRadius='5'
                        class='article'
                        on:tap={() => showDrink(search)}>
                        <label 
                            textwrap="{true}"
                            class='h2 text-center white'
                            text='{search.strDrink}'
                            />
                        <image 
                            class='img-rounded img' 
                            src='{search.strDrinkThumb}' 
                            alt='cover' 
                            stretch='aspectFill' 
                            />
                    </stackLayout>  
                    {/each} 
            {:else}
                {#each drinks as drink}
                    <stackLayout 
                        borderColor='lightyellow'
                        borderWidth='5'
                        borderRadius='5'
                        class='article'
                        on:tap={() => showDrink(drink)}>
                        <label 
                            textwrap="{true}"
                            class='h2 text-center white'
                            text='{drink.strDrink}'
                            />
                        <image 
                            class='img-rounded img' 
                            src='{drink.strDrinkThumb}' 
                            alt='cover' 
                            stretch='aspectFill' 
                            />
                    </stackLayout>   
                {:else}
                <activityIndicator busy={true}/>
            {/each}
            {/if}       
        </stackLayout>
    </scrollView>
</stackLayout>