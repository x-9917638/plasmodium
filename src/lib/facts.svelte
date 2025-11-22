<script lang="ts">
    import error from '$lib/assets/error.svg';

    type Fact = {
        title: string;
        body: string;
        icon?: string;
        image?: string;
    };

    let {
        fact = {
            title: 'No fact provided',
            body: 'Pass a `fact` prop with title, body, and optional media.',
            icon: error
        },
        align = 'left'
    }: { fact?: Fact; align?: 'left' | 'right' } = $props();

    const media = fact.image ?? fact.icon ?? error;
</script>

<section class="facts">
        <article class={`fact-card ${align === 'right' ? 'fact-card--flip' : ''}`}>
            <div class="fact-text">
                <h3>{fact.title}</h3>
                <p>{fact.body}</p>
            </div>
            <div class="fact-media">
                <img src={media} alt={fact.title} />
            </div>
        </article>
</section>

<style>
    .facts {
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
        max-width: 960px;
        margin: 0 auto;
        padding: 1rem;
    }

    .fact-card {
        display: flex;
        gap: 2rem;
        padding: 1.5rem;
        background: #020617;
        border-radius: 1rem;
        border: 1px solid rgba(255, 255, 255, 0.08);
        color: #f1f5f9;
        align-items: center;
        box-shadow: 0 1rem 2.5rem rgba(15, 23, 42, 0.35);

    }

    .fact-card:hover {
        box-shadow: 0 1.75rem 3.5rem rgba(15, 23, 42, 0.45);
        transform: translateY(-6px) scale(1.02);
        border-color: rgba(94, 234, 212, 0.5);
        transition: transform .1s;
    }

    .fact-card--flip {
        flex-direction: row-reverse;
        text-align: right;
    }

    .fact-text {
        flex: 1 1 300px;
    }

    .fact-text h3 {
        font-size: 1.65rem;
        margin-bottom: 0.5rem;
    }

    .fact-text p {
        line-height: 1.5;
        font-size: 1.05rem;
        color: rgba(241, 245, 249, 0.88);
    }

    .fact-media {
        flex: 1 1 280px;
        border-radius: 0.75rem;
        overflow: hidden;
        background: #020617;
    }

    .fact-media img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        display: block;
    }


    /* Fineeee I'll try to support mobile */
    @media (max-width: 768px) {
        .fact-card,
        .fact-card--flip {
            flex-direction: column;
            text-align: left;
        }

        .fact-media,
        .fact-text {
            width: 100%;
        }
    }
</style>