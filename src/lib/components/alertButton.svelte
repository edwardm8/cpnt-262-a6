<script>
  import {createEventDispatcher} from 'svelte'

  const dispatch = createEventDispatcher()
  export let buttonText;
  
  function eventClickMe() {
   dispatch('message', {
    text:"No coupons available at the moment"}
    );
  }
</script>

<!-- dispatch event -->
<section class="m-auto text-center">
  <button on:click={eventClickMe} class="bg-blue-200 p-2">{buttonText}</button>
</section>
