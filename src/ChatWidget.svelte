<script>
    import { fade } from 'svelte/transition';

    export let showChat = false;
    export let messages = [];
    export let loadingResponse = false;

    let container;

    function toggleChat() {
        showChat = !showChat
    }

</script>
<div class="chat-widget-container">
    {#if showChat}
        <div class="chat-container">
        </div>
    {/if}
    <vwc-fab connotation="cta" on:click={toggleChat} icon="chat-2-line"></vwc-fab>
</div>
<style>
    .chat-container {
        box-shadow: 0 0 20px 0 rgb(0 0 0 / 20%);
        width: 449px;
        max-height: 600px;
        height: 600px;
        border-radius: 18px;
        background: white;
        margin: 10px;
    }
</style>