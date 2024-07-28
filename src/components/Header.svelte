<script>
    export let navigate;
</script>

<style>
    header {
        background-color: #007bff;
        padding: 20px;
        color: #fff;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    header .logo {
        font-size: 1.5em;
        font-weight: bold;
        cursor: pointer;
    }
    header nav {
        display: flex;
        gap: 20px;
    }
    header nav a {
        color: #fff;
        text-decoration: none;
        font-size: 1em;
        transition: color 0.3s ease;
        cursor: pointer;
    }
    header nav a:hover {
        color: #d0d0d0;
    }
    header .cart {
        display: flex;
        align-items: center;
        font-size: 1.5em;
        cursor: pointer;
    }
    header .cart svg {
        width: 24px;
        height: 24px;
        fill: #fff;
        transition: fill 0.3s ease;
    }
    header .cart:hover svg {
        fill: #d0d0d0;
    }
</style>

<header>
    <div class="logo" on:click={() => navigate('home')}>Loja Online</div>
    <nav>
        <a on:click={() => navigate('home')}>Home</a>
        <a on:click={() => navigate('cart')}>Carrinho</a>
    </nav>
    <div class="cart" on:click={() => navigate('cart')}>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M7 18c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zm10 0c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2zM7.82 14l-.82-4H18V8H7.16l-.82-4H3v2h2.24l1.4 6.97L5.82 16H18v-2H7.82z"/></svg>
    </div>
</header>
