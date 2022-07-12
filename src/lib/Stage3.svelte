<script lang="ts">
    import { fade } from "svelte/transition";
    import ad from "../assets/ad.png";

    let adLoaded = false;

    export let stage: number;
    export let cookiesAccepted: boolean;
</script>

<div class="modal" out:fade>
    <h1 class="title">Complete Cookie Configuration</h1>

    <div class="wrapper">
        <div class="decline-wrapper">
            <button class="decline-button" on:click={() => stage++}>
                Decline</button
            >
        </div>
        <button
            class="accept-button one"
            on:click={() => (cookiesAccepted = true)}>Accept</button
        >
        <button
            class="accept-button two"
            on:click={() => (cookiesAccepted = true)}>Accept</button
        >
        <button
            class="accept-button three"
            on:click={() => (cookiesAccepted = true)}>Accept</button
        >
        <button
            class="accept-button four"
            on:click={() => (cookiesAccepted = true)}>Accept</button
        >
        <button
            class="accept-button five"
            on:click={() => (cookiesAccepted = true)}>Accept</button
        >
    </div>
</div>

<style scoped>
    @keyframes moveVertically {
        0% {
            transform: translateY(0);
        }
        50% {
            transform: translateY(100px);
        }
        100% {
            transform: translateY(0%);
        }
    }
    @keyframes moveHorizontally {
        0% {
            transform: translateX(0);
        }
        25% {
            transform: translateX(-250px);
        }
        75% {
            transform: translateX(250px);
        }
        100% {
            transform: translateX(0);
        }
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

    .wrapper {
        position: relative;
        width: 100%;
        height: 200px;
        padding: 0 36px;
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        align-items: center;
    }

    .accept-button {
        border: none;
        background-color: var(--primary-color);
        color: white;
        border-radius: 8px;
        font-size: 1.5em;
        margin-bottom: 96px;
        padding: 16px 24px;
        animation: moveVertically 2s linear infinite;
    }

    .accept-button.two {
        animation-delay: -0.2s;
        animation-duration: 1.2s;
    }
    .accept-button.three {
        animation-delay: -1.2s;
        animation-duration: 1.1s;
    }
    .accept-button.four {
        animation-delay: -2.2s;
        animation-duration: 1.5s;
    }
    .accept-button.five {
        animation-delay: -3.2s;
        animation-duration: 2.1s;
    }

    .accept-button:hover {
        cursor: pointer;
        filter: brightness(1.1);
    }

    .decline-wrapper {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    .decline-button {
        opacity: 0.3;
        border: none;
        background-color: var(--decline-color);
        color: white;
        border-radius: 8px;
        font-size: 1.2em;
        padding: 8px 16px;
        animation: moveHorizontally 2s linear infinite;
    }

    .decline-button:hover {
        cursor: pointer;
        filter: brightness(1.1);
    }
</style>
