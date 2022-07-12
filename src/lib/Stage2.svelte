<script lang="ts">
    import { fade } from "svelte/transition";
    import ad from "../assets/ad.png";

    let adLoaded = false;

    export let stage: number;
    export let cookiesAccepted: boolean;
</script>

<div class="modal" out:fade>
    <h1 class="title">Verify Selection</h1>
    {#if !adLoaded}
        <div class="loading" />
    {/if}
    {#if adLoaded}
        <img src={ad} alt="Advertisement" height="300" />
    {/if}
    <button class="accept-button" on:click={() => (cookiesAccepted = true)}
        >Accept Cookies</button
    >
    <button
        class="decline-button"
        on:click={() => stage++}
        on:pointerenter={() => (adLoaded = true)}
    >
        Verify</button
    >
</div>

<style scoped>
    @keyframes spin {
        0% {
            transform: rotateY(0deg);
        }
        24% {
            background-image: url("/cookie_icon.png");
        }
        25% {
            transform: rotateY(90deg);
            background-image: url("/cookie_icon_reversed.png");
        }
        50% {
            transform: rotateY(180deg);
        }
        74% {
            background-image: url("/cookie_icon_reversed.png");
        }
        75% {
            background-image: url("/cookie_icon.png");
            transform: rotateY(270deg);
        }
        100% {
            transform: rotateY(360deg);
        }
    }
    .loading {
        width: 50px;
        height: 50px;
        margin-bottom: 20px;
        display: grid;
        place-items: center;
        background-image: url("/cookie_icon.png");
        background-repeat: no-repeat;
        background-size: 100% auto;
        animation: spin 2s infinite linear;
    }
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
        opacity: 0.3;
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
