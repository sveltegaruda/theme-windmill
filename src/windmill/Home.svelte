<script>
    // export let location
    import { onMount } from 'svelte'

    onMount(() => {
        let els = document.querySelectorAll("li.nav-sidemenu a");
        els = document.querySelectorAll("li.nav-sidemenu span.nav-sidemenu-active");
        for (let i = 0; i < els.length; i++) {
            els[i].className = "nav-sidemenu-active";
        }
    })

    let pageName = "Home";
</script>

<main>
    <h1>Hello <span style="color:#333;text-decoration: underline;">{pageName}</span> Page!</h1>
    <p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
</main>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }

    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>
