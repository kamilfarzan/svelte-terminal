<script>
  import Entry from "./Entry.svelte";
  let entries = [];
  let initVal = "";
  let initValH3 = "";
  let boolForFirst = false;

  function handleSubmit(e) {
    console.log(entries);
    entries.push({ text: e.detail.text });
    entries = entries;
    if (e.detail.text === "clear") {
      entries = [];
      initVal = "";
      initValH3 = "";
      boolForFirst = false;
    }
  }
</script>

<Entry
  bind:entry={initVal}
  bind:output={initValH3}
  bind:booleanCondition={boolForFirst}
  on:submit={handleSubmit}
/>
{#each entries as entry, i (i)}
  <Entry on:submit={handleSubmit} />
{/each}
