<script lang="ts">
    import { fade } from "svelte/transition";
    import ad from "../assets/ad.png";

    let adLoaded = false;

    export let stage: number;
    export let cookiesAccepted: boolean;
</script>

<div class="modal" out:fade>
    <h1 class="title">Complete Cookie Configuration</h1>

    <canvas />
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
</style>
