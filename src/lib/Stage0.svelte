<script lang="ts">
    import { fade } from "svelte/transition";

    export let stage: number;
    export let cookiesAccepted: boolean;
</script>

<div class="modal" out:fade>
    <h1 class="title">Cookies enhance your experience!</h1>
    <br />
    <div class="description">
        Not actually, but it does help us profit through
    </div>
    <div class="description">
        targeted advertising, selling data, and other wonderful things.
    </div>
    <br />
    <button class="accept-button" on:click={() => (cookiesAccepted = true)}>
        Accept All Cookies!</button
    >
    <button class="decline-button" on:click={() => stage++}>Customize</button>
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

    .description {
        font-size: 1.3em;
        color: white;
        opacity: 0.3;
        margin: px 0;
    }

    .accept-button {
        border: none;
        background-color: var(--primary-color);
        color: white;
        border-radius: 8px;
        font-size: 1.5em;
        margin-top: 16px;
        padding: 16px 24px;
    }

    .accept-button:hover {
        cursor: pointer;
        filter: brightness(1.1);
    }

    .decline-button {
        border: none;
        background: none;
        color: white;
        border-radius: 8px;
        font-size: 1em;
        margin-top: 24px;
        margin-bottom: 20px;
        text-decoration: underline;
    }

    .decline-button:hover {
        cursor: pointer;
        filter: brightness(1.1);
    }
</style>
