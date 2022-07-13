<script lang="ts">
    import { fade } from "svelte/transition";
    import Accepted from "./Accepted.svelte";
    import Declined from "./Declined.svelte";
    import Stage0 from "./Stage0.svelte";
    import Stage1 from "./Stage1.svelte";
    import Stage2 from "./Stage2.svelte";
    import Stage3 from "./Stage3.svelte";
    import Stage4 from "./Stage4.svelte";
    let cookiesAccepted = false;
    let stage = 5;
</script>

<main>
    {#if !cookiesAccepted && stage !== 5}
        <div class="modal-wrapper" out:fade>
            {#if stage === 0}
                <Stage0 bind:stage bind:cookiesAccepted />
            {/if}
            {#if stage === 1}
                <Stage1 bind:stage bind:cookiesAccepted />
            {/if}
            {#if stage === 2}
                <Stage2 bind:stage bind:cookiesAccepted />
            {/if}
            {#if stage === 3}
                <Stage3 bind:stage bind:cookiesAccepted />
            {/if}
            {#if stage === 4}
                <Stage4 bind:stage bind:cookiesAccepted />
            {/if}
        </div>
    {/if}
    {#if cookiesAccepted}
        <Accepted bind:cookiesAccepted />
    {/if}
    {#if stage === 5}
        <Declined bind:stage />
    {/if}
</main>

<style>
    .modal-wrapper {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        z-index: 9999;
    }
</style>
