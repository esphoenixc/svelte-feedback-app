<script>
  import FeedbackForm from "./components/FeedbackForm.svelte";
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";

  let feedback = [
    {
      id: 1,
      rating: 10,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 2,
      rating: 9,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 3,
      rating: 8,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
  ];

  $: count = feedback.length;
  $: average =
    feedback.reduce((prev, { rating }) => prev + rating, 0) / feedback.length;

  const deleteFeedback = (e) => {
    const itemId = e.detail;
    //이 {} 감싼 filter는 무조건 return을 해줘야 함 아니면 한꺼번에 다 지워짐 ;;;
    // feedback = feedback.filter((item) => {
    //   return item.id != itemId;
    // });
    console.log(itemId);

    feedback = feedback.filter((item) => item.id != itemId);
  };

  const addFeedback = (e) => {
    const newFeedback = e.detail;

    feedback = [newFeedback, ...feedback];
  };
</script>

<main class="container">
  <FeedbackForm on:add-feedback={addFeedback} />
  <FeedbackStats {count} {average} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>
