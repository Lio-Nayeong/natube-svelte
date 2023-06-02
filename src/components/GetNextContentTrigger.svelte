<script>
  import { inview } from "svelte-inview";
  export let getNextContent;
</script>

<div
  use:inview={{
    rootMargin: "20%",
  }}
  on:inview_change={getNextContent}
/>
