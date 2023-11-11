<script>
  import {createEventDispatcher} from 'svelte'

  const dispatch = createEventDispatcher()

  function eventClickMe() {
   dispatch('message', {
    text:"Special toppings added"}
    );
  }
</script>

<section class="m-auto text-center">
  <h2>Special Toppings</h2>
  <button on:click|once={eventClickMe} class="bg-blue-200 p-2">Add</button>
</section>
