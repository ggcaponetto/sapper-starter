<script>
    function handleMessage(event) {
        alert(event.detail.text);
    }

    let Game;
    setTimeout(() => {
        import('./game.svelte').then(({default: gameModule}) => {
            console.log("loaded game module", gameModule);
            Game = gameModule;
        });
    }, 0)
</script>

<style>
    :global(html, body, #sapper, main){
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
    }
</style>
{#if Game}
    <Game on:message={handleMessage}/>
{:else}
    <div>loading...</div>
{/if}
