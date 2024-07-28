<script>
    let items = [
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
</script>

<main>
    <h1>Loja Online</h1>
    <div class="items">
        {#each items as item}
            <div class="item">
                <img src={item.image_url} alt={item.name} />
                <h2>{item.name}</h2>
                <p>{item.description}</p>
                <p class="price">{item.currency} {item.price.toFixed(2)}</p>
                {#if item.in_stock}
                    <button class="buy">Comprar</button>
                {:else}
                    <button class="buy" disabled>Indisponível</button>
                {/if}
            </div>
        {/each}
    </div>
</main>

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
    .items {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        gap: 20px;
    }
    .item {
        border: 1px solid #e0e0e0;
        border-radius: 10px;
        padding: 20px;
        text-align: center;
        background-color: #fff;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
    }
    .item:hover {
        transform: translateY(-10px);
        box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
    }
    .item img {
        width: 100%;
        height: auto;
        border-radius: 10px;
        margin-bottom: 15px;
    }
    .item h2 {
        font-size: 1.5em;
        margin-bottom: 10px;
        color: #333;
    }
    .item p {
        font-size: 1em;
        color: #666;
    }
    .item .price {
        font-size: 1.2em;
        color: #000;
        margin: 15px 0;
    }
    .buy {
        padding: 10px 20px;
        font-size: 1em;
        color: #fff;
        background-color: #007bff;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }
    .buy:hover {
        background-color: #0056b3;
    }
    .buy:disabled {
        background-color: #ccc;
        cursor: not-allowed;
    }
</style>
