<script>
    import { onMount } from 'svelte';

    let cartItems = [
        {
            id: 1,
            name: "Smartphone XYZ",
            description: "Um smartphone com excelente custo-benefício e ótimo desempenho.",
            price: 1499.99,
            currency: "BRL",
            image_url: "https://example.com/images/smartphone_xyz.jpg",
            quantity: 1
        },
        {
            id: 2,
            name: "Notebook ABC",
            description: "Notebook de alta performance ideal para trabalho e jogos.",
            price: 2999.99,
            currency: "BRL",
            image_url: "https://example.com/images/notebook_abc.jpg",
            quantity: 1
        }
    ];

    let total = 0;

    const calculateTotal = () => {
        total = cartItems.reduce((acc, item) => acc + item.price * item.quantity, 0);
    };

    const removeItem = (id) => {
        cartItems = cartItems.filter(item => item.id !== id);
        calculateTotal();
    };

    const increaseQuantity = (id) => {
        const item = cartItems.find(item => item.id === id);
        item.quantity += 1;
        calculateTotal();
    };

    const decreaseQuantity = (id) => {
        const item = cartItems.find(item => item.id === id);
        if (item.quantity > 1) {
            item.quantity -= 1;
        } else {
            removeItem(id);
        }
        calculateTotal();
    };

    onMount(() => {
        calculateTotal();
    });
</script>

<style>
    main {
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
    .cart-items {
        display: grid;
        grid-template-columns: 1fr;
        gap: 20px;
    }
    .cart-item {
        display: flex;
        align-items: center;
        border: 1px solid #e0e0e0;
        border-radius: 10px;
        padding: 20px;
        background-color: #fff;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
    .cart-item img {
        width: 100px;
        height: auto;
        border-radius: 10px;
        margin-right: 20px;
    }
    .cart-item-info {
        flex: 1;
    }
    .cart-item-info h2 {
        font-size: 1.5em;
        margin-bottom: 10px;
        color: #333;
    }
    .cart-item-info p {
        font-size: 1em;
        color: #666;
    }
    .cart-item-price {
        font-size: 1.2em;
        color: #000;
    }
    .cart-item-quantity {
        display: flex;
        align-items: center;
        gap: 10px;
        margin-top: 10px;
    }
    .cart-item-quantity button {
        padding: 5px 10px;
        font-size: 1em;
        color: #fff;
        background-color: #007bff;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }
    .cart-item-quantity button:hover {
        background-color: #0056b3;
    }
    .cart-item-quantity span {
        font-size: 1em;
        color: #333;
    }
    .cart-item-remove {
        padding: 5px 10px;
        font-size: 1em;
        color: #fff;
        background-color: #ff0000;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }
    .cart-item-remove:hover {
        background-color: #cc0000;
    }
    .total {
        text-align: right;
        font-size: 1.5em;
        color: #333;
        margin-top: 20px;
    }
</style>

<main>
    <h1>Carrinho de Compras</h1>
    <div class="cart-items">
        {#each cartItems as item}
            <div class="cart-item">
                <img src={item.image_url} alt={item.name} />
                <div class="cart-item-info">
                    <h2>{item.name}</h2>
                    <p>{item.description}</p>
                    <p class="cart-item-price">{item.currency} {item.price.toFixed(2)}</p>
                    <div class="cart-item-quantity">
                        <button on:click={() => decreaseQuantity(item.id)}>-</button>
                        <span>{item.quantity}</span>
                        <button on:click={() => increaseQuantity(item.id)}>+</button>
                    </div>
                    <button class="cart-item-remove" on:click={() => removeItem(item.id)}>Remover</button>
                </div>
            </div>
        {/each}
    </div>
    <div class="total">Total: BRL {total.toFixed(2)}</div>
</main>
