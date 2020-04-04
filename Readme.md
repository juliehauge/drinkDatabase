# Cocktail Recipes App
This is a simple App for IOS that connects to an <a href='https://www.thecocktaildb.com/api.php'>API</a> with a fetch call, to display a list of drinks. With the navigation bar, one can navigate between each page where the different drink recipes are displayed. One is also able to search for a specific drink on each page.

It uses the <a href='https://svelte-native.technology/docs'>svelte-native</a> framework to build a native application. Svelte-native to build on top of <a href='https://nativescript.org'>Nativescript</a>, so you need to go through the setup guide there in order to install the TNS CLI tools.

## Set up
```html
npm install
tns run ios

```

## Project Structure
This is a five page application, where each page is imported in app/App.svelte. 
Each page:
- fetches data from an API in the svelte onMount function
- uses a <a href='https://svelte-native.technology/docs#scrollview'>scrollView</a> to display a scrollable list of drinks
- uses an <a href='https://svelte.dev/docs#each'>each</a> block to display each drink in the API in a list
- uses a <a href='https://svelte-native.technology/docs#searchbar'>searchBar</a> component for entering search phrases
- the <a href='https://svelte-native.technology/docs#searchbar'>searchBar</a> binds the text for the searchPhrase, and uses a filter-function on the drinks, to display the name of the drink searched for
- when providing a search phrase, the function only filters the drink if the name of the alcohol-type is not included, for example: search for Smash, not Gin Smash
- uses an on:tap function to display a component with information on the recipe, with a <a href='https://svelte-native.technology/docs#showmodal'>showModal</a> function
- uses an <a href='https://svelte-native.technology/docs#closemodal'>closeModal</a> function that closes the component and current modal view

In the app/App.svelte:
- the pages are imported in a <a href='https://svelte-native.technology/docs#bottom-navigation'>botttomNavigation</a> component
- the <a href='https://svelte-native.technology/docs#tabcontentitem'>tabContentItem</a> contains the display view of each page, with a <a href='https://svelte-native.technology/docs#navigate'>navigate</a> function to navigate between the pages
