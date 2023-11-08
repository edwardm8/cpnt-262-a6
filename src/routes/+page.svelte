<script>
    import OrderList from "../lib/components/orderList.svelte";

  let info = [
    {
      name: "Bob",
      toppings: ["Pepperoni"," Cheese"," Ham"],
      drink: "beer"
    },
    {
      name: "Charles",
      toppings: ["Cheese"],
      drink: "Coke"
    },
    {
      name: "Luke",
      toppings: ["Pepperoni"," Cheese"," Onions"," Green Peppers"],
      drink: "Water"
    }
  ];
    let newName
    let toppings = []
 const addItem = function updateList(event){
    info = [...info,{name:newName,toppings:toppings}]
}
</script>

<h2>Order</h2>
<input bind:value={newName} placeholder="enter your name" />
<label><input type="checkbox" bind:group={toppings} value={"Pepperoni"} />Pepperoni</label>
<label><input type="checkbox" bind:group={toppings} value={"Cheese"} />Cheese</label>
<label><input type="checkbox" bind:group={toppings} value={"Mushrooms"} />Mushrooms</label>
<button on:click={addItem}>Order</button>


<h1>Current orders</h1>
{#each info as orders}
<p>{orders.name} has orderd pizza with {orders.toppings} and a {orders.drink}.</p>
{/each}



