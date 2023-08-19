<script>
  import { createEventDispatcher } from "svelte";
  import data from "./data.json";

  export let entry = "";
  export let output = "";

  const dispatch = createEventDispatcher();
  export let booleanCondition = false;

  function relayToParent() {
    if (entry === "help") {
      output = data.help;
    } else if (entry === "about") {
      output = data.about;
    } else if (entry === "github") {
      window.open("https://github.com/kmlfrzn", "_blank").focus();
      output = data.github;
    } else if (entry === "clear") {
      output = "";
    } else {
      output = data.error;
    }
    booleanCondition = true;
    dispatch("submit", { text: entry });
  }
</script>

<div>
  <form on:submit|preventDefault={relayToParent}>
    <label for="in"><span>$</span> :: ></label>
    <!-- svelte-ignore a11y-autofocus -->
    <input
      type="text"
      bind:value={entry}
      disabled={booleanCondition}
      autofocus={true}
    />
  </form>
  <h4 class="output">{output}</h4>
</div>

<style>
  @font-face {
    font-family: "FiraCode";
    src: url("/FiraCode.ttf") format("ttf");
  }
  span {
    text-shadow: 0 0 10px rgba(255, 0, 0, 0.5);
    font-weight: 500;
    color: red;
  }
  label {
    font-size: medium;
  }
  input {
    font-size: medium;
    font-weight: 500;
    font-family: "Fira Code", monospace;
    width: 50%;
    outline: none;
    border: none;
    background: none;
    color: hsl(0, 0%, 90%);
  }
  .output {
    text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
    font-weight: 500;
    white-space: pre-line;
  }
</style>
