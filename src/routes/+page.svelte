<script>

  import PizzaList from '$lib/components/newOptions.svelte'

  let info = [
    {
      name: "Bob",
      toppings: ["Pepperoni"," Cheese"," Ham"]
   
    },
    {
      name: "Charles",
      toppings: ["Cheese"]
    },
    {
      name: "Luke",
      toppings: ["Pepperoni"," Cheese"," Onions"," Green Peppers"]
    }
  ];
  let newName
  let toppings = []
  let listShow = false
    

  function addItem(event){
    info = [...info,{name:newName,toppings:toppings}]
  }

</script>

<section class="p-4 flex flex-col">
  <h2 class="m-auto text-2xl">Order</h2>
  <!-- Inline function -->
  <button on:click={() => {
    if(listShow == false)
      listShow = true
    else if (listShow == true)
      listShow = false}} 
    class="bg-blue-400 p-4 max-w-xl m-auto">Show
  </button>

  <!-- topping list render -->
  <div class="flex flex-col m-auto">
    <label>Name <input bind:value={newName} placeholder="Enter your name"/></label>
    <label>Toppings</label>
    <label><input type="checkbox" bind:group={toppings} value={"Pepperoni"} />Pepperoni</label>
    <label><input type="checkbox" bind:group={toppings} value={"Cheese"} />Cheese</label>
    <label><input type="checkbox" bind:group={toppings} value={"Mushrooms"} />Mushrooms</label>
    <!-- toggle special toppings -->
    {#if listShow === true}
      <label><input type="checkbox" bind:group={toppings} value={"Chocolate"} />Chocolate</label>
      <label><input type="checkbox" bind:group={toppings} value={"Gummies"} />Gummies</label>
    {/if} 

    <!-- coupon button using components for step 2 and 3-->
    <PizzaList/>
    <button class="bg-blue-400 p-4" on:click={addItem}>Order</button>
  </div>
</section>

<section class="flex p-4 flex-col">
  <h2 class="m-auto text-2xl">Current orders</h2>
  {#each info as orders,i}
    <p class="m-auto">{orders.name} has orderd pizza with {orders.toppings}.</p>
  {/each}
</section>
