<script>
  export const { articleText } = $props();
</script>

<div class="article-text">
  <p>{articleText}</p>
</div>

<style>
  .article-text {
    padding: 50px; /* Add space inside the box on all sides */
    margin: 50vh auto; /* Add vertical space between items, and center horizontally */
    width: 70%; /* Base width of the text box, responsive */
    max-width: 32vw; /* Prevent the text box from getting too wide on large screens */
    box-shadow: 16px 16px #007052; /* Box shadow */
    border-radius: 0px 64px;
    border-color: #e3ff00;
    border-style: solid;
    border-width: 4px;
    background-color: var(--color, #8aa6df);
  }

  /* .article-text.active  {
        background-color: #f7f5eb;
    }

     .article-text.inactive {
        background-color: #8aa6df;
    } */
</style>
