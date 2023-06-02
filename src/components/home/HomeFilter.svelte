<script>
  export let filter;
  export let text;
  // export let onClickFilter;
</script>

<button class={filter === text ? "black" : "gray"}>
  {text}
</button>

<style>
  .black {
    background-color: #030303;
    color: white;
  }
  .gray {
    background-color: #f2f2f2;
  }

  .black,
  .gray {
    border: none;
    border-radius: 8px;
    padding: 6px 12px;
    margin: 12px;
    margin-left: 0;
    cursor: pointer;
  }
</style>
