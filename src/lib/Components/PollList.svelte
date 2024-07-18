<script>
  import { fade, scale, slide } from "svelte/transition";
  import { flip } from "svelte/animate";
  import pollStore from "../Stores/PollStore";
  import PollDetails from "./PollDetails.svelte";

  // Log the pollStore to ensure it's reactive
  $: console.log($pollStore);
</script>

<div class="poll-list">
  {#each $pollStore as poll (poll.id)}
    <div in:fade out:scale|local animate:flip={{ duration: 500 }}>
      <PollDetails {poll} />
    </div>
  {/each}
</div>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }
</style>
