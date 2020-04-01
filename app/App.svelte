
<script>
    import { navigate } from 'svelte-native'
    import Drink from './modals/Drink.svelte'
    import Vodka from './pages/Vodka.svelte'
    import Tequila from './pages/Tequila.svelte'
    import Gin from './pages/Gin.svelte'
    import Rum from './pages/Rum.svelte' 
    import Home from './pages/Home.svelte'
</script>

<page>

   <actionBar 
        backgroundColor='lightyellow'
        flat='true'>
        <label 
            text='Drink Recipes' 
            textTransform='uppercase' 
            fontWeight='400'
            fontSize='24'
           />
    </actionBar>
    
 
    <bottomNavigation>
        <tabStrip backgroundColor='lightyellow'>
            <tabStripItem>
                <label class='navText home' text="Home" />	
            </tabStripItem>
            <tabStripItem>
                <label class='navText' text="Gin" />	
            </tabStripItem>
            <tabStripItem >
                <label class='navText' text="Vodka"/>
            </tabStripItem>
            <tabStripItem >
                <label class='navText' text="Tequila" />
            </tabStripItem>
            <tabStripItem >
                <label class='navText' text="Rum" />
            </tabStripItem>
        </tabStrip>

        <tabContentItem > 
            <stackLayout>
            <Home on:tap={() => navigate({ page: Home})}/>
            </stackLayout>
        </tabContentItem>

        <tabContentItem > 
            <stackLayout>
            <Gin on:tap={() => navigate({ page: Gin})}/>
            </stackLayout>
        </tabContentItem>

        <tabContentItem>
           <stackLayout>
            <Vodka on:tap={() => navigate({ page: Vodka})}/>
            </stackLayout>
        </tabContentItem>
        
        <tabContentItem>
           <stackLayout>
            <Tequila on:tap={() => navigate({ page: Tequila})}/>
            </stackLayout>
        </tabContentItem>

        <tabContentItem>
            <stackLayout>
            <Rum on:tap={() => navigate({ page: Rum})}/>
            </stackLayout>
        </tabContentItem> 
    </bottomNavigation>
</page>


<style>
    .navText{
        text-transform: uppercase;
        font-weight: 400;
    }
    .home{
        font-weight: 700;
    }
</style>