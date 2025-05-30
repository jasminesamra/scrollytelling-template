<script>
  // destructuring: take the element called "children" from props and assign it to the variable children
  export const { children, articleTexts } = $props();
  console.log(children);
</script>

<div>
  <div>
    {#each articleTexts as articleText}
      <p class="article-text">{articleText}</p>
    {/each}
  </div>
</div>

<style>
  .article-text {
    background-color: #f7f5eb;
    padding: 50px;
    margin-top: 50vh;
    margin-bottom: 100vh;
  }
</style>
