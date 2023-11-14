<script>
  import Button from '$lib/components/alertButton.svelte'
 
  // render popup
  function handleMessage(event) {
    alert(event.detail.text)
  }
</script>

<!-- Step 4 using buttonText prop-->
<Button on:message={handleMessage} buttonText="Coupons"/>



