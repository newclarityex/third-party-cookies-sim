<script lang="ts">
    import cookies from "./assets/cookies.jpg";
    import Modal from "./lib/Modal.svelte";
</script>

<main>
    <!-- <Modal /> -->
    <header>
        <div class="title">My amazing website</div>
        <nav>
            <a href=".">Home</a>
            <a href=".">About</a>
            <a href=".">Contact</a>
        </nav>
    </header>
    <div class="article-wrapper">
        <article>
            <h1>Clickbait Title</h1>
            <address>Written by Some Random Intern</address>
            <br />
            <div class="image-wrapper">
                <img
                    class="article-image"
                    src={cookies}
                    alt="Cookies and Milk"
                />
            </div>
            <p>
                Lorem ipsum dolor sit amet. Vel magni animi est corrupti
                repudiandae et molestiae dolor et voluptate libero et quaerat
                alias et sequi repellendus. Qui ipsa doloribus 33 autem neque
                sit nemo voluptatem?
            </p>
            <p>
                Est modi officiis id corporis inventore eos fugit sint ut amet
                atque. Et veniam deleniti aut excepturi similique quo sint
                soluta ut porro impedit qui similique quia 33 quaerat autem sed
                rerum sunt. Est quae ullam vel amet dolore ex quasi numquam et
                nostrum quam qui soluta laudantium internos nam repellat neque.
                Id galisum nisi sed mollitia debitis rem dolor maiores?
            </p>
            <p>
                Ut possimus debitis in deleniti optio in doloribus obcaecati aut
                repudiandae dolorem quo modi quaerat vel quod consequatur. Quo
                quod numquam sed autem dolorum qui deleniti voluptatem qui
                maxime itaque sed numquam beatae eum amet illo. Aut odio
                quisquam At blanditiis similique qui similique inventore qui
                nobis internos? Est odio obcaecati et accusantium minus sed
                ducimus voluptatem vel sequi accusantium.
            </p>
            <p>
                Ut provident aliquid non natus omnis ex alias aliquid in harum
                odio. Aut necessitatibus obcaecati non facere repellat ex
                possimus labore eum asperiores porro quo dolorem aliquid sit
                saepe necessitatibus non ipsam repellendus? Hic possimus sequi
                eos aperiam error et veniam voluptas in quia tempora.
            </p>
        </article>
    </div>
</main>

<style>
    :root {
        --primary-color: #00bd9d;
        --secondary-color: #5f634f;
        --tertiary-color: #f5f5f5;
    }

    header {
        line-height: 64px;
        background-color: var(--primary-color);
        color: white;
        padding: 1rem;
        text-align: center;
        font-weight: 500;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
    }

    .article-wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    article {
        padding: 36px 0;
        width: 80%;
        max-width: 100ch;
    }

    .title {
        margin: 0 36px;
        font-size: 2.5rem;
    }

    nav > a {
        text-decoration: none;
        color: white;
        font-size: 2rem;
        margin: 0 36px;
    }

    h1 {
        font-size: 2rem;
        color: var(--secondary-color);
        margin: 16px 0;
    }

    address {
        font-size: 1.2rem;
        color: var(--secondary-color);
        margin: 0;
    }

    .image-wrapper {
        box-sizing: border-box;
        width: 100%;
        padding: 36px;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .article-image {
        max-width: 80%;
    }

    p {
        margin: 28px 0;
        text-indent: 64px;
        font-size: 1.3rem;
        line-height: 32px;
    }
</style>
