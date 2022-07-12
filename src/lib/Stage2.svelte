<script lang="ts">
    import { fade } from "svelte/transition";
    import ad from "../assets/ad.png";

    let adLoaded = false;

    export let stage: number;
    export let cookiesAccepted: boolean;
</script>

<div class="modal" out:fade>
    <h1 class="title">Verify Selection</h1>
    <br />
    {#if adLoaded}
        <img src={ad} alt="Advertisement" height="250" />
    {/if}
    <button class="accept-button" on:click={() => (cookiesAccepted = true)}
        >Accept Cookies</button
    >
    <button
        class="decline-button"
        on:click={() => stage++}
        on:pointerenter={() => (adLoaded = true)}
    >
        Decline</button
    >
</div>

<style scoped>
    .modal {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 600px;
        background-color: var(--tertiary-color);
        padding: 20px;
        border-radius: 0.5rem;
        box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.2);
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .title {
        text-align: center;
        color: white;
    }

    img {
        margin-bottom: 20px;
    }

    .accept-button {
        border: none;
        background-color: var(--primary-color);
        color: white;
        border-radius: 8px;
        font-size: 1.5em;
        margin-bottom: 96px;
        padding: 16px 24px;
    }

    .accept-button:hover {
        cursor: pointer;
        filter: brightness(1.1);
    }

    .decline-button {
        border: none;
        background-color: var(--decline-color);
        color: white;
        border-radius: 8px;
        font-size: 1.2em;
        padding: 8px 16px;
        margin: 10px;
    }

    .decline-button:hover {
        cursor: pointer;
        filter: brightness(1.1);
    }
</style>
