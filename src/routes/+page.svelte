<script lang="ts">
  import { invoke } from "@tauri-apps/api/core";

  let name = $state("");
  let greetMsg = $state("");

  async function greet(event: Event) {
    event.preventDefault();
    // Learn more about Tauri commands at https://tauri.app/develop/calling-rust/
    greetMsg = await invoke("greet", { name });
  }
</script>

<main class="container">
  <div class="quote_header">
    <div class="quote_header_col1">
      <p class="quote_header_option_label">Quoted To:</p>
      <div class="quote_header_option_quoted_to">
        <input id="quoted_to_name" class="quote_header_option_input"/>
        <input id="quoted_to_city" class="quote_header_option_input"/>
        <input id="quoted_to_state" class="quote_header_option_input"/>
        <p>Rep:</p>
        <input id="quoted_to_rep" class="quote_header_option_input"/>
      </div>
      <p class="quote_header_option_label">Attn:</p>
      <input id="attn" class="quote_header_option_input"/>
      <p class="quote_header_option_label">Project:</p>
      <input id="project" class="quote_header_option_input"/>
      <p class="quote_header_option_label">Specifier:</p>
      <input id="specifier" class="quote_header_option_input"/>
      <p class="quote_header_option_label">POC:</p>
      <input id="poc" class="quote_header_option_input"/>
      <p class="quote_header_option_label">GPO Name:</p>
      <input id="gpo_name" class="quote_header_option_input"/>
    </div>
    <!-- <div class="quote_header_col2">
      <p class="quote_header_option_label">Quote No:</p>
      <div class="quote_header_option_quoted_number">
        <input id="quote_no" class="quote_header_option_input"/>
        <input id="quoted_no_rev" class="quote_header_option_input"/>
      </div>
      <p class="quote_header_option_label">Attn:</p>
      <input id="attn" class="quote_header_option_input"/>
      <p class="quote_header_option_label">Project:</p>
      <input id="project" class="quote_header_option_input"/>
      <p class="quote_header_option_label">Specifier:</p>
      <input id="specifier" class="quote_header_option_input"/>
      <p class="quote_header_option_label">POC:</p>
      <input id="poc" class="quote_header_option_input"/>
      <p class="quote_header_option_label">GPO Name:</p>
      <input id="gpo_name" class="quote_header_option_input"/>
    </div> -->
    <!-- <p class="quote_header_option_label">Quoted To:</p>
    <input class="quote_header_option_input"/>
    <p class="quote_header_option_label">Quoted To:</p>
    <input class="quote_header_option_input"/> -->
  </div>
  <!-- <form class="row" onsubmit={greet}>
    <input id="greet-input" placeholder="Enter a name..." bind:value={name} />
    <button type="submit">Greet</button>
  </form>
  <p>{greetMsg}</p> -->
</main>

<style>
.logo.vite:hover {
  filter: drop-shadow(0 0 2em #747bff);
}

.logo.svelte-kit:hover {
  filter: drop-shadow(0 0 2em #ff3e00);
}

.quote_header {
  display: grid;
  grid-template-columns: [col1] 33% [col2] 33% [col3] 33%;
  grid-template-rows: [row1] 100%;
}

.quote_header_col1 {
    display: grid;
    gap: 5px;
    grid-template-columns: [col1] 50% [col2] 50%;
}

.quote_header_col2 {
    display: grid;
    gap: 5px;
    grid-template-columns: [col1] 50% [col2] 50%;
}

.quote_header_option_label {
  padding-right: 5px;
  padding-left: 5px;
  align-self: center;
}

.quote_header_option_quoted_to {
  display: grid;
  gap: 2px;
  grid-template-columns: [col1] 40% [col2] 20% [col3] 20% [col4] 20%;
  grid-template-rows: [row1] 50% [row2] 50%; 
}

.quote_header_option_input {
  border-radius: 4px;
  border: 1px solid transparent;
  padding: 0.1em;
  padding-left: 5px;

  font-family: inherit;
  color: #0f0f0f;
  background-color: #ffffff;
  transition: border-color 0.25s;
  box-shadow: 0 2px 2px rgba(0, 0, 0, 0.2);
}

.quote_header_option_quoted_number {
  grid-template-rows: [row1] 50% [row2] 50%; 
}

#quoted_to_name {
  grid-column-start: 1;
  grid-column-end: 5;
}

#quoted_to_city {

}

#quoted_to_state {

}

#quoted_to_rep {

}


:root {
  font-family: Inter, Avenir, Helvetica, Arial, sans-serif;
  font-size: 16px;
  line-height: 24px;
  font-weight: 400;

  color: #0f0f0f;
  background-color: #f6f6f6;

  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-text-size-adjust: 100%;
}

.container {
  margin: 0;
  padding-top: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  width: 100%;
}

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: 0.75s;
}

.row {
  display: flex;
  justify-content: center;
}



/* input,
button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  color: #0f0f0f;
  background-color: #ffffff;
  transition: border-color 0.25s;
  box-shadow: 0 2px 2px rgba(0, 0, 0, 0.2);
} */

button {
  cursor: pointer;
}

button:hover {
  border-color: #396cd8;
}
button:active {
  border-color: #396cd8;
  background-color: #e8e8e8;
}

input,
button {
  outline: none;
}

#greet-input {
  margin-right: 5px;
}

@media (prefers-color-scheme: dark) {
  :root {
    color: #f6f6f6;
    background-color: #2f2f2f;
  }

  a:hover {
    color: #24c8db;
  }

  input,
  button {
    color: #ffffff;
    background-color: #0f0f0f98;
  }
  button:active {
    background-color: #0f0f0f69;
  }
}

</style>
