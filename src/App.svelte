<script>

    // -- IMPORTS

    import Header from "./components/Header.svelte";
    import { fly } from "svelte/transition";
    import { circInOut } from "svelte/easing";

    // -- VARIABLES

    let drink = 'coffee';

    // -- FUNCTIONS

    function rotate()
    {
        drink = drink === 'coffee' ? 'milk' : 'coffee';
    }
</script>

<style lang="stylus">
    // -- STYLES

    article
    {
        margin: 0;
        width: 100%;
        padding: 0;

        display: flex;
        flex-direction: column;

        background-color: #EAD4C3;

        font-family: Arial, sans-serif;
    }

    article.milk
    {
        background-color: #FEF9ED;
    }

    main
    {
        width: 100%;
        height: 93vh;
        min-height: 600px;
        margin-top: 7vh;

        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .drink
    {
        width: 100%;

        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;

        .can
        {
            position: relative;

            height: 25rem;
            width: 20rem;

            background-image: url("https://aroma-coffee.vercel.app/images/can.svg");
            background-repeat: no-repeat;
            background-position: center;

            img
            {
                position: absolute;

                height: 100%;
                width: 100%;
            }

            img.content
            {
                padding: 3.5rem 0 0;
                height: 70%;
            }
        }

        button
        {
            position: fixed;
            bottom: 5vh;

            min-width: 20vw;
            padding: 0.5rem 1rem;

            font-size: 1.2rem;
            font-weight: bold;
            color: #333;

            background-color: transparent;

            border: 1px solid #333;
            border-radius: 1rem;

            cursor: pointer;
        }
    }

    h1
    {
        position: fixed;

        font-size: 30vh;
        max-font-size: 20rem;
        color: #8D5B33;
    }

    h1.milk
    {
        color: #363234;
    }
</style>

<svelte:head>
    <title>Aroma Coffee</title>
    <link rel="icon" href="https://aroma-coffee.vercel.app/images/favicon.ico">
</svelte:head>

<article class:milk={ drink === 'milk' }>
    <Header />
    <main>
        <section class="drink">
            { #if drink === 'coffee' }
                <h1 transition:fly={ { delay: 0, duration: 1000, x: -50, y: 0, opacity: 0, easing: circInOut } }>Café</h1>
            { :else }
                <h1 class="milk" transition:fly={ { delay: 0, duration: 1000, x: 50, y: 0, opacity: 0, easing: circInOut } }>Leite</h1>
            { /if }
            <div class="can">
                { #if drink === 'coffee' }
                    <img
                        class="content"
                        src="images/coffee_can_content.svg"
                        alt="Café can content"
                        transition:fly={ { delay: 0, duration: 1000, x: -50, y: 0, opacity: 0, easing: circInOut } }
                    />
                    <img
                        src="images/coffee_can_outside.svg"
                        alt="Café can outside"
                        transition:fly={ { delay: 0, duration: 1000, x: -50, y: 0, opacity: 0, easing: circInOut } }
                    />
                { :else }
                    <img
                        class="content"
                        src="images/milk_can_content.svg"
                        alt="Leite can content"
                        transition:fly={ { delay: 0, duration: 1000, x: 50, y: 0, opacity: 0, easing: circInOut } }
                    />
                    <img
                        src="images/milk_can_outside.svg"
                        alt="Leite can outside"
                        transition:fly={ { delay: 0, duration: 1000, x: 50, y: 0, opacity: 0, easing: circInOut } }
                    />
                { /if }
            </div>
            <button on:click={ rotate }>
                Slide
            </button>
        </section>
    </main>
</article>
