<script>
  import axios from "axios";
  import { onMount, afterUpdate } from "svelte";
  // import { inview } from "svelte-inview";
  import Layout from "../components/UI/Layout.svelte";
  import Card from "../components/home/HomeCard.svelte";
  import EmptyCard from "../components/home/HomeCardLoading.svelte";
  import GetNextContentTrigger from "../components/GetNextContentTrigger.svelte";

  const apiKey = import.meta.env.VITE_API_KEY;

  let isMounted = true;
  let pageCount = 0;
  let cards = [];

  onMount(() => {
    getContent(30);
  });

  async function getContent(itemCount) {
    try {
      const response = await axios.get(
        "https://www.googleapis.com/youtube/v3/videos",
        {
          params: {
            part: "snippet,statistics",
            chart: "mostPopular",
            regionCode: "KR",
            maxResults: itemCount,
            key: apiKey,
          },
        }
      );
      pageCount++;
      cards = [...cards, ...response.data.items];
      isMounted = true;
    } catch (e) {
      console.error("error : ", e);
    }
  }
  const getNextContent = ({ detail }) => {
    if (!detail.inView) {
      return;
    }
    if (5 <= pageCount) {
      // console.log(`getNextContent - reached the last page.`);
      return;
    }
    getContent(20);
  };
</script>

<Layout activeMenu="home">
  <div class="container">
    <div class="grid">
      {#if isMounted}
        {#each cards as data}
          <Card {data} {apiKey} />
        {/each}
        <GetNextContentTrigger {getNextContent} />
      {:else}
        {#each Array(50).fill({}) as _, _}
          <EmptyCard />
        {/each}
      {/if}
    </div>
  </div>
</Layout>

<style>
  .container {
    padding: 24px 36px 24px 24px;
  }
  .grid {
    display: grid;
    width: 100%;
    row-gap: 40px;
    column-gap: 16px;
    grid-template-columns: repeat(auto-fit, minmax(300px, auto));
  }
</style>
