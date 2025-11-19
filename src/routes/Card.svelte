<script lang="ts">
    let { href, title, description } = $props();
</script>

<a href={href} aria-label="Link to {href}"><div class="card">
    <h1>{title}</h1>
    <p>{description}</p>
</div></a>

<style>
    .card {
        height: 300px;
        padding: 20px;
        border-radius: 20px;
        border: 2px solid white;
        background-color: black;
    }
    h1 {
        font-size: 50px;
        color: white;
        font-family: 'JetBrains Mono', monospace;
    }
    p {
        font-size: 20px;
        color: white;
        font-family: 'JetBrains Mono', monospace;
    }
</style>