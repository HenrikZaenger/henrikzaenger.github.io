<script>
    import Card from './Card.svelte'
    let cards = [
        {
            href: "/binary",
            title: "Binary tools",
            description: "Tools for converting numbers"
        }
    ]
    export const prerender = true
</script>

<div id="grid">
    {#each cards as card}
    <Card href={card.href} title={card.title} description={card.description}></Card>
    {/each}
</div>

<style>
    #grid {
        padding: 20px;
        width: 100%;
        height: 100vh;
        display: grid;
        gap: 10px;
        background-color: black;
    }
    @media (orientation: landscape) {
        #grid {
            grid-template-columns: 33% 33% 33%;
        }
    }
    @media (orientation: portrait) {
        #grid {
            grid-template-columns: 100%;
        }
    }
</style>