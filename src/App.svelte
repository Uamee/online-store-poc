<script>
    import Header from './components/Header.svelte';
    import ItemList from './components/ItemList.svelte';
    import Cart from './components/Cart.svelte';

    let page = 'home';

    const items = [
        {
            id: 1,
            name: "Smartphone XYZ",
            description: "Um smartphone com excelente custo-benefício e ótimo desempenho.",
            price: 1499.99,
            currency: "BRL",
            image_url: "https://example.com/images/smartphone_xyz.jpg",
            in_stock: true
        },
        {
            id: 2,
            name: "Notebook ABC",
            description: "Notebook de alta performance ideal para trabalho e jogos.",
            price: 2999.99,
            currency: "BRL",
            image_url: "https://example.com/images/notebook_abc.jpg",
            in_stock: true
        },
        {
            id: 3,
            name: "Fone de Ouvido Bluetooth",
            description: "Fone de ouvido sem fio com excelente qualidade de som.",
            price: 199.99,
            currency: "BRL",
            image_url: "https://example.com/images/fone_bluetooth.jpg",
            in_stock: false
        }
    ];

    function navigate(target) {
        page = target;
    }
</script>

<Header {navigate} />

{#if page === 'home'}
    <main>
        <h1>Loja Online</h1>
        <ItemList {items} />
    </main>
{:else if page === 'cart'}
    <Cart />
{/if}

<style>
    main {
        font-family: 'Helvetica Neue', Arial, sans-serif;
        padding: 20px;
        max-width: 1200px;
        margin: auto;
    }
    h1 {
        text-align: center;
        margin-bottom: 40px;
        font-size: 2.5em;
        color: #333;
    }
</style>
