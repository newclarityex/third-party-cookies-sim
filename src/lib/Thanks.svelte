<div class="wrapper">
    <div class="popup">
        Thanks for allowing third party cookies! 🎉 <div class="background" />
    </div>
</div>

<style scoped>
    .wrapper {
        width: 100%;
        height: 100%;
        pointer-events: none;
    }
    .popup {
        position: fixed;
        bottom: 20px;
        right: 20px;
        border: var(--secondary-color) solid 4px;
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
        background-color: var(--secondary-color);
        opacity: 0.8;
    }
</style>
