<script>
  import { afterUpdate, tick, onMount } from "svelte";

  let y = 0;

  onMount(() => {
    window.addEventListener("scroll", handleScroll);
  });

  function handleScroll() {
    let scrollTop = window.pageYOffset;
    let innerHeight = window.innerHeight;
    let scrollHeight = document.documentElement.scrollHeight;
    if (scrollTop + innerHeight >= scrollHeight) {
      console.log("스크롤 바닥");
    }
  }
</script>

<div>
  <div class="box" />
</div>
<svelte:window bind:scrollY={y} />

<style>
  .box {
    background-color: #f9f9f9;
    height: 2000px;
    padding-top: 12px;
    box-sizing: border-box;
  }
</style>
