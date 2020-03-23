
<script>
    import {onMount} from 'svelte'
    import {showModal} from 'svelte-native'
    import {navigate} from 'svelte-native'
    import Drink from './modals/Drink.svelte' 
    import Vodka from './Vodka.svelte'
    import Tequila from './Tequila.svelte'
    import Gin from './Gin.svelte'
    import Rum from './Rum.svelte'
  
</script>

<page>
    <actionBar backgroundColor='lightyellow'>
    <stackLayout orientation="vertical">
        <label 
            text='Drink Recipes' 
            fontSize='24' 
            padding='0'
            textTransform='uppercase' 
            fontWeight='400' 
            verticalAlignment="center"/>  
    </stackLayout> 
    </actionBar>
  

    <bottomNavigation>
        <tabStrip backgroundColor='lightyellow'>
            <tabStripItem>
                <label class='navText' text="Gin" />	
            </tabStripItem>
            <tabStripItem class="special">
                <label class='navText' text="Vodka"/>
            </tabStripItem>
            <tabStripItem class="special">
                <label class='navText' text="Tequila" />
            </tabStripItem>
            <tabStripItem class="special">
                <label class='navText' text="Rum" />
            </tabStripItem>
        </tabStrip>

        <tabContentItem>
            <Gin on:tap='{() => navigate({ page: Gin})}'/>
        </tabContentItem>

        <tabContentItem>
            <Vodka on:tap='{() => navigate({ page: Vodka})}'/>
        </tabContentItem>
        
        <tabContentItem>
            <Tequila on:tap='{() => navigate({ page: Tequila})}'/>
        </tabContentItem>

        <tabContentItem>
            <Rum on:tap='{() => navigate({ page: Rum})}'/>
        </tabContentItem>
    </bottomNavigation>
</page>


<style>
    .navText{
        text-transform: uppercase;
        font-weight: 600;
    }
</style>