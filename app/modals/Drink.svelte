<script>
    import { Template } from 'svelte-native/components'
    import {closeModal} from 'svelte-native'

    export let drink
</script>

<frame>
    <page>
        <scrollView>
            <stackLayout style="padding:24">
                <textField class="h1" text={drink.strDrink} />
                <label 
                    class="p" 

                    textwrap="{true}"
                    text={drink.strInstructions} />
                <label
                    class='body text-center white'
                    text='{drink.strGlass}'
                    /> 
             
                <textField class='h3' text="{drink.strMeasure1}{drink.strIngredient1}" />
                <textField class='h3' text="{drink.strMeasure2}{drink.strIngredient2}" />
                <textField class='h3' text="{drink.strMeasure3}{drink.strIngredient3}" />
                <textField class='h3' text="{drink.strIngredient4}" />
                <textField class='h3' text="{drink.strIngredient5}" />
		              
	               
                <button on:tap={() => closeModal()} text='close' />
            </stackLayout>
        </scrollView>
    </page>
</frame>


<style>
    .h1{
        padding: 5;
        text-transform: uppercase;
        font-weight: 200;
        font-size: 24;

    }
    .body{
       padding-top: 10;
    }
    .p{
       padding: 10 22;
    }
</style>