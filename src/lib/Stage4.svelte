<script lang="ts">
    import { onMount, onDestroy } from "svelte/internal";
    import { fade } from "svelte/transition";
    import generator from "generate-maze";
    import cookieIcon from "../assets/cookie_icon.png";

    export let stage: number;
    export let cookiesAccepted: boolean;

    const mazeWidth = 18;
    const mazeHeight = 9;
    const maze = generator(mazeWidth, mazeHeight, true, Math.random());

    const size = 30;

    const offset = [20, 30];
    let velocity = [0, 0];
    let position = [0.4, 0.1];
    let displayPosition = [
        position[0] * size + offset[0],
        position[1] * size + offset[1],
    ];

    const keys = {
        ArrowUp: false,
        ArrowDown: false,
        ArrowLeft: false,
        ArrowRight: false,
    };

    function handleKeyDown(event: KeyboardEvent) {
        event.preventDefault();
        keys[event.key] = true;
    }

    function handleKeyUp(event: KeyboardEvent) {
        event.preventDefault();
        keys[event.key] = false;
    }

    function checkCollision(oldPosition: number[], newPosition: number[]) {
        if (
            newPosition[0] < 0 ||
            newPosition[0] >= mazeWidth ||
            newPosition[1] < 0 ||
            newPosition[1] > mazeHeight
        ) {
            return true;
        }
        const oldX = Math.floor(oldPosition[0]);
        const newX = Math.floor(newPosition[0]);
        const oldY = Math.floor(oldPosition[1] + 0.5);
        const newY = Math.floor(newPosition[1] + 0.5);

        if (newX > oldX && maze[oldY][oldX].right) {
            return true;
        }
        if (newX < oldX && maze[oldY][oldX].left) {
            return true;
        }
        if (newY > oldY && maze[oldY][oldX].bottom) {
            return true;
        }
        if (newY < oldY && maze[oldY][oldX].top) {
            return true;
        }
    }

    const acceleration = 0.01;
    const friction = 0.999;
    const maxVelocity = 3;
    function updateLocation() {
        if (keys.ArrowUp && velocity[1] < maxVelocity) {
            velocity[1] -= acceleration;
        } else if (keys.ArrowDown) {
            velocity[1] += acceleration;
        } else {
            velocity[1] = velocity[1] * friction;
        }
        if (keys.ArrowLeft && velocity[0] < maxVelocity) {
            velocity[0] -= acceleration;
        } else if (keys.ArrowRight) {
            velocity[0] += acceleration;
        } else {
            velocity[0] = velocity[0] * friction;
        }

        const newPosition = [
            position[0] + velocity[0],
            position[1] + velocity[1],
        ];

        if (checkCollision(position, newPosition)) {
            velocity = [0, 0];
            cookiesAccepted = true;
            return;
        }

        if (newPosition[0] > mazeWidth - 1 && newPosition[1] > mazeHeight - 2) {
            stage++;
            window.removeEventListener("keydown", handleKeyDown);
            window.removeEventListener("keyup", handleKeyUp);
            window.clearInterval(movementInterval);
        }

        position = newPosition;
        displayPosition[0] = position[0] * 30 + offset[0];
        displayPosition[1] = position[1] * 30 + offset[1];
        velocity = velocity.map((x) => x * 0.95);
    }

    let movementInterval: number;
    onMount(() => {
        window.addEventListener("keydown", handleKeyDown);
        window.addEventListener("keyup", handleKeyUp);
        movementInterval = window.setInterval(updateLocation, 1000 / 60);
    });
    onDestroy(() => {
        window.removeEventListener("keydown", handleKeyDown);
        window.removeEventListener("keyup", handleKeyUp);
        window.clearInterval(movementInterval);
    });
</script>

<div class="modal" in:fade out:fade>
    <h1 class="title">Complete Cookie Configuration</h1>
    <p class="description">Cross a line to accept, use arrow keys.</p>
    <div class="maze-wrapper">
        <div
            class="player"
            style="transform: translate({displayPosition[0]}px, {displayPosition[1]}px);"
        >
            <img src={cookieIcon} alt="Player" class="player-icon" />
        </div>
        <div class="goal">x</div>
        <svg width="600" height="330">
            {#each maze as row}
                <g transform="translate(30, 30)">
                    {#each row as cell}
                        {#if cell.top}
                            <line
                                x1={cell.x * size}
                                y1={cell.y * size}
                                x2={cell.x * size + size}
                                y2={cell.y * size}
                                stroke="#00bd9d"
                                stroke-width={2}
                                stroke-linecap="round"
                            />
                        {/if}
                        {#if cell.bottom}
                            <line
                                x1={cell.x * size}
                                y1={cell.y * size + size}
                                x2={cell.x * size + size}
                                y2={cell.y * size + size}
                                stroke="#00bd9d"
                                stroke-width={2}
                                stroke-linecap="round"
                            />
                        {/if}
                        {#if cell.left}
                            <line
                                x1={cell.x * size}
                                y1={cell.y * size}
                                x2={cell.x * size}
                                y2={cell.y * size + size}
                                stroke="#00bd9d"
                                stroke-width={2}
                                stroke-linecap="round"
                            />
                        {/if}
                        {#if cell.right}
                            <line
                                x1={cell.x * size + size}
                                y1={cell.y * size}
                                x2={cell.x * size + size}
                                y2={cell.y * size + size}
                                stroke="#00bd9d"
                                stroke-width={2}
                                stroke-linecap="round"
                            />
                        {/if}
                    {/each}
                </g>
            {/each}
        </svg>
    </div>
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

    .player {
        width: 25px;
        height: 25px;
        position: absolute;
    }
    .player::before {
        position: absolute;
        content: "";
        margin: 10px;
        width: 5px;
        height: 5px;
        border-radius: 50%;
        background-color: yellow;
    }

    .player-icon {
        height: 100%;
        width: 100%;
    }

    .goal {
        text-align: center;
        line-height: 20px;
        color: white;
        position: absolute;
        bottom: 58px;
        right: 55px;
        width: 20px;
        height: 20px;
        background-color: var(--decline-color);
        border-radius: 50%;
    }
</style>
