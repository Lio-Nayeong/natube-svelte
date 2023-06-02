<script>
  import Header from "./Header.svelte";
  import Menu from "./Menu.svelte";

  export let activeMenu;
  // $: console.log(activeMenu);

  let menu = true;
  // $: menu = true;

  function toggleMenu() {
    menu = !menu; // on,off 개념 boolean
  }
</script>

<div class="container">
  <Header {toggleMenu} />
  <div class="layout">
    {#if menu}
      <Menu {activeMenu} />
    {/if}
    <div class={menu ? "contents" : "offMenu"}>
      <slot />
    </div>
  </div>
</div>

<style>
  .container {
    display: flex;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    overflow: overlay;
    flex-direction: column;
  }
  .layout {
    display: flex;
    flex: 1;
    margin-top: 56px;
    /* border: 5px solid skyblue; */
  }
  .contents {
    flex: 1;
    margin-left: 240px;
    /* border: 5px solid lightcoral; */
  }
  .offMenu {
    flex: 1;
    margin-left: 0px;
  }
  @media screen and (max-width: 990px) {
    .contents {
      margin-left: 72px;
    }
  }
  @media screen and (max-width: 620px) {
    .contents {
      margin-left: 0px;
    }
  }
</style>
