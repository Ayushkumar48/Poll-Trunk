<script>
  import Header from "./lib/Components/Header.svelte";
  import Footer from "./lib/Components/Footer.svelte";
  import Tabs from "./lib/Shared/Tabs.svelte";
  import CreatePollForm from "./lib/Components/CreatePollForm.svelte";
  import PollList from "./lib/Components/PollList.svelte";
  let items = ["Current Polls", "Add New Poll"];
  let activeItem = "Current Polls";
  const tabChange = (e) => {
    activeItem = e.detail;
  };

  const handleAdd = (e) => {
    activeItem = "Current Polls";
  };
</script>

<Header />
<main>
  <Tabs {items} {activeItem} on:tabChange={tabChange} />
  {#if activeItem === "Current Polls"}
    <PollList />
  {:else if activeItem === "Add New Poll"}
    <CreatePollForm on:add={handleAdd} />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
