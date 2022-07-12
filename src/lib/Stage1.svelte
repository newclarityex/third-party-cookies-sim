<script lang="ts">
    import { fade } from "svelte/transition";

    let totalUnchecked = 0;
    let expanded = false;

    function handleCheckboxChange(event: Event) {
        const checkbox = event.target as HTMLInputElement;
        totalUnchecked += checkbox.checked ? -1 : 1;
        if (totalUnchecked === 3) {
            expanded = true;
        }
    }

    export let stage: number;
    export let cookiesAccepted: boolean;
</script>

<div class="modal" in:fade out:fade>
    <h1 class="title">Customize Cookies</h1>
    <br />
    <ul>
        <li>
            <div>Necessary Cookies</div>
            <input
                type="checkbox"
                on:input={handleCheckboxChange}
                disabled={true}
                checked
            />
        </li>
        <li>
            <div>Marketing and Advertising</div>
            <input type="checkbox" on:input={handleCheckboxChange} checked />
        </li>
        <li>
            <div>Metrics</div>
            <input type="checkbox" on:input={handleCheckboxChange} checked />
        </li>
        <li>
            <div>Personalization</div>
            <input type="checkbox" on:input={handleCheckboxChange} checked />
        </li>
        {#if expanded}
            <li>
                <div>Name and Location Tracking</div>
                <input
                    type="checkbox"
                    on:input={handleCheckboxChange}
                    checked
                />
            </li>
            <li>
                <div>Your Identity and Soul</div>
                <input
                    type="checkbox"
                    on:input={handleCheckboxChange}
                    checked
                />
            </li>
        {/if}
    </ul>
    <button class="accept-button" on:click={() => (cookiesAccepted = true)}>
        Accept All</button
    >
    <button
        class="continue-button"
        on:click={() => {
            if (totalUnchecked === 5) {
                stage++;
            } else {
                cookiesAccepted = true;
            }
        }}>Continue with Selection</button
    >
</div>

<style scoped>
    .modal {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 700px;
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

    .accept-button {
        border: none;
        background-color: var(--primary-color);
        color: white;
        border-radius: 8px;
        font-size: 1.5em;
        padding: 16px 24px;
        margin: 0;
        margin-bottom: 20px;
    }

    button:hover {
        cursor: pointer;
        filter: brightness(1.1);
    }

    ul {
        width: 600px;
        list-style: none;
    }

    li {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        color: white;
        font-size: 1.5em;
        margin: 32px 0;
    }

    input[type="checkbox"] {
        position: relative;
        width: 40px;
        height: 40px;
        background-color: #205d83;
        border-radius: 8px;
        appearance: none;
        outline: 0;
    }

    input[type="checkbox"]:hover {
        cursor: pointer;
    }

    input[type="checkbox"]::after {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        content: "";
        display: block;
        background-color: white;
        width: 100%;
        height: 100%;
        border-radius: 8px;
        transition: 0.25s;
    }

    input[type="checkbox"]:checked::after {
        width: 0;
        height: 0;
        border-radius: 50%;
    }

    input[type="checkbox"]:disabled {
        opacity: 0.4;
    }

    .continue-button {
        position: absolute;
        bottom: 20px;
        right: 20px;
        border: none;
        background: none;
        color: white;
        border-radius: 8px;
        font-size: 1em;
        opacity: 0.3;
    }
</style>
