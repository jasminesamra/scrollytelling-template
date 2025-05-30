<script>
  // destructuring: take the element called "children" from props and assign it to the variable children
  export const { children, background, articleTexts } = $props();
</script>

<div class="scroller">
  <div class="background">
    {@render background()}
  </div>
  <div class="foreground">
    {#each articleTexts as articleText}
      <p class="article-text">{articleText}</p>
    {/each}
  </div>
</div>

<style>
  .scroller {
    position: relative; /* Allows child elements with absolute or sticky positioning to position relative to this container */
    height: auto; /* Let the container grow based on its content's height */
  }

  .background {
    position: sticky; /* Keeps the background element fixed in place while scrolling until its parent is out of view */
    top: 0; /* Stick to the top of the viewport */
    height: 100vh; /* Make the background fill the full height of the viewport */
    z-index: 0; /* Place it behind other elements (foreground should have a higher z-index) */
    background: #ff99fc; /* Set a background color (can be removed if an image or component is rendered) */
    display: flex; /* Use flexbox to easily center child content */
    align-items: center; /* Vertically center any content inside the background */
    justify-content: center; /* Horizontally center any content inside the background */
    width: 50vw; /* Set background width to half the viewport width */
  }

  .foreground {
    position: relative; /* Stack on top of the background while still flowing in document order */
    z-index: 1; /* Ensure foreground content sits above the sticky background */
    width: 100%; /* Make foreground take up the full width of its container */
  }

  .article-text {
    background-color: #8aa6df; /* Light blue background color for the text box */
    padding: 50px; /* Add space inside the box on all sides */
    margin: 50vh auto; /* Add vertical space between items, and center horizontally */
    width: 70%; /* Base width of the text box, responsive */
    max-width: 40vw; /* Prevent the text box from getting too wide on large screens */
  }
</style>
