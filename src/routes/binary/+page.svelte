<script lang="ts">
    import { onMount } from 'svelte';


    import Output from './Output.svelte';

    let selectedOption = 'hex';
    let input = ''

    onMount(() => {
        const match = document.cookie.match(/selectedOption=([^;]+)/);
        if (match) selectedOption = match[1];
    });

    function handleChange() {
        document.cookie = `selectedOption=${selectedOption}; path=/; max-age=${60*60*24*365}`;
    }

    export const prerender = true
</script>

<div id="center">
    <div id="flex">
        <div id="left">
            <select name="format" id="format" bind:value={selectedOption} on:change={handleChange}>
                <option value="bin">Binary</option>
                <option value="dec">Decimal</option>
                <option value="hex">Hexadecimal</option>
            </select>
            <input type="text" name="input" id="input" bind:value={input}>
        </div>
        <div id="right">
            <Output input={input} format={selectedOption}></Output>
        </div>
    </div>
</div>

<style>
    #center {
        display: grid;
        place-items: center;
        width: 100%;
        height: 100vh;
        background-color: black;
    }
    #flex {
        display: flex;
        flex-direction: row;
        width: 75%;
        height: 75%;
        border: 2px solid white;
        border-radius: 20px;
        padding: 20px;
        color: white;
        font-family: 'JetBrains Mono', monospace;
        font-size: 20px;
    }
    #left {
        display: flex;
        flex-direction: column;
        gap: 10px;
        width: 50%;
        height: 100%;
        padding: 2%;
    }
    #right {
        display: flex;
        flex-direction: column;
        gap: 10px;
        width: 50%;
        height: 100%;
        padding: 2%;
    }
    input {
        border: 2px solid white;
        outline: none;
        padding: 2px
    }
    select {
        background-color: black;
    }
</style>