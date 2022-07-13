<script lang="ts">
    export let stage: number;
</script>

<div class="wrapper">
    <div class="popup">
        You've declined our third party cookies ;(
        <br />
        <button on:click={() => (stage = 0)}>Return to Configuration</button>
        <div class="background" />
    </div>
</div>

<style scoped>
    .wrapper {
        width: 100%;
        height: 100%;
        pointer-events: none;
    }
    .popup {
        pointer-events: auto;
        position: fixed;
        bottom: 20px;
        right: 20px;
        border: var(--decline-color) solid 4px;
        color: white;
        padding: 12px 20px;
        font-size: 1.5em;
        font-weight: 500;
        border-radius: 8px;
    }
    .background {
        z-index: -1;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: var(--decline-color);
        opacity: 0.8;
    }
    button {
        width: 100%;
        font-size: 0.8em;
        text-decoration: underline;
        text-align: center;
        border: none;
        background: none;
        color: white;
    }
    button:hover {
        cursor: pointer;
    }
</style>
