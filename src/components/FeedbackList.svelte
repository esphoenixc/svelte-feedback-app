<script>
  //   import { onMount, onDestroy } from "svelte";
  import { FeedbackStore } from "../stores";
  import { fade, scale } from "svelte/transition";
  import FeedbackItem from "./FeedbackItem.svelte";

  //라이프 사이클을 이용하여 피드백을 스토어로부터 가져오고 파괴하기 onDestory
  //   let feedback = [];

  //   const unsubscribe = FeedbackStore.subscribe((data) => (feedback = data));

  //   onMount(() => {
  //     console.log("mounted");
  //   });

  //   onDestroy(() => {
  //     unsubscribe();
  //   });
</script>

{#each $FeedbackStore as fb (fb.id)}
  <!--  Cool transition, MUST WRAP IN A DIV!!!!!!-->
  <!-- <div transition:fade> -->
  <div in:scale out:fade={{ duration: 500 }}>
    <FeedbackItem item={fb} />
  </div>
{/each}
