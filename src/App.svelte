<script lang="ts">
  import { Router, Route } from "svelte-routing";
  import Home from "./pages/Home.svelte";
  import Subscription from "./pages/Subscription.svelte";
  import Trending from "./pages/Trending.svelte";
  import Music from "./pages/Music.svelte";
</script>

<main>
  <Router>
    <Route path="/" component={Home} />
    <Route path="/subscription" component={Subscription} />
    <Route path="/trending" component={Trending} />
    <Route path="/music" component={Music} />
  </Router>
</main>
