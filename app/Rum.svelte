<script>
    import {onMount} from 'svelte'
    import {showModal} from 'svelte-native'
    import {navigate} from 'svelte-native'
    import Drink from './modals/Drink.svelte' 
  
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
</script>

<stackLayout>
    <scrollView>
        <stackLayout class='articles'>
            {#each drinks as drink}
                <stackLayout 
                    class='article'
                    on:tap={() => showDrink(drink)}>
                    <label 
                        textwrap="{true}"
                        class='h2 text-center white'
                        text='{drink.strDrink}'
                        />
                    <image 
                        class='img-rounded' 
                        src='{drink.strDrinkThumb}' 
                        alt='cover' 
                        stretch='aspectFill' 
                        />
                </stackLayout>   
            {:else}
                <activityIndicator busy={true}/>
            {/each}         
        </stackLayout>
    </scrollView>
</stackLayout>