<script>
  import SecretPizza from '$lib/components/alertButton.svelte'

  let info = [
    {
      name: "Bob",
      toppings: ["Pepperoni"," Cheese"," Ham"],
    },
    {
      name: "Charles",
      toppings: ["Cheese"],
    },
    {
      name: "Luke",
      toppings: ["Pepperoni"," Cheese"," Onions"," Green Peppers"],
    }
  ];
    let newName
    let toppings = []
    let special = false

  function addItem(event){
    info = [...info,{name:newName,toppings:toppings}]
  }

  function handleMessage(event) {
    alert(event.detail.text)
    special = true
  }

</script>

<section class="p-4 flex flex-col">
  <h2 class="m-auto text-2xl">Order</h2>
  <SecretPizza on:message={handleMessage}/>
  <div class="flex flex-col m-auto">
    <label>Name <input bind:value={newName} placeholder="enter your name"/></label>
    <label>Toppings</label>
    <label><input type="checkbox" bind:group={toppings} value={"Pepperoni"} />Pepperoni</label>
    <label><input type="checkbox" bind:group={toppings} value={"Cheese"} />Cheese</label>
    <label><input type="checkbox" bind:group={toppings} value={"Mushrooms"} />Mushrooms</label>
    {#if special === true}
      <label><input type="checkbox" bind:group={toppings} value={"Chocolate"} />Chocolate</label>
      <label><input type="checkbox" bind:group={toppings} value={"Gummies"} />Gummies</label>
    {/if}
    <button class="bg-blue-400 p-4" on:click={addItem}>Order</button>
  </div>
</section>

<section class="flex p-4 flex-col">
  <h2 class="m-auto text-2xl">Current orders</h2>
  {#each info as orders}
  <p class="m-auto">{orders.name} has orderd pizza with {orders.toppings}.</p>
  {/each}
</section>
