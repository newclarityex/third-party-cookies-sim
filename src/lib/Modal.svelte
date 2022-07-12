<script lang="ts">
    let cookiesAccepted = false;
    function acceptCookies() {
        cookiesAccepted = true;
    }
</script>

<main>
    {#if !cookiesAccepted}
        <div class="modal-wrapper">
            <div class="modal">
                <h1 class="modal-title">Cookies enhance your experience!</h1>
                <br />
                <div class="modal-description">
                    Not actually, but it does help us profit through
                </div>
                <div class="modal-description">
                    targeted advertising, selling data, and other wonderful
                    things.
                </div>
                <br />
                <button class="accept-button" on:click={acceptCookies}
                    >Accept All Cookies!</button
                >
                <button class="decline-button">Customize</button>
            </div>
        </div>
    {/if}
</main>

<style scoped>
    .modal-wrapper {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        z-index: 9999;
    }

    .modal {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 80%;
        max-width: 800px;
        background-color: var(--tertiary-color);
        padding: 20px;
        border-radius: 0.5rem;
        box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.2);
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .modal-title {
        text-align: center;
        color: white;
    }

    .modal-description {
        font-size: 1.3em;
        color: white;
        opacity: 0.3;
        margin: 8px 0;
    }

    .accept-button {
        border: none;
        background-color: var(--primary-color);
        color: white;
        border-radius: 8px;
        font-size: 1.5em;
        margin-top: 36px;
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
    }

    .decline-button:hover {
        cursor: pointer;
        filter: brightness(1.1);
    }
</style>
