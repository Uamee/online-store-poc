<script>
    export let items;
</script>

<style>
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
