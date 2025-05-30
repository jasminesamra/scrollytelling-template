<script>
  import { onMount } from 'svelte';
  import ArticleTextBox from './ArticleTextBox.svelte';

  export const { children, background, articleTexts } = $props();

  let intersectionObserver;
  let articleTextElements;
  let areElementsActive = $state([]);

  onMount(() => {
    const createIntersectionObserver = () => {
      const options = {
        threshold: [0.8, 0.9, 0.95, 1]
      };

      const callback = (entries, observer) => {
        entries.forEach((entry) => {
          const elem = entry.target;

          if (entry.intersectionRatio >= 0.9) {
            elem.style.backgroundColor = '#f7f5eb'; //todo: this should be set within the child component via a prop (but this is a good intermediate step before refactoring to show)
          } else if (entry.intersectionRatio < 0.9) {
            elem.style.backgroundColor = '#8aa6df';
          }
        });
      };

      intersectionObserver = new IntersectionObserver(callback, options);
    };
    createIntersectionObserver();

    articleTextElements = [...document.getElementsByClassName('article-text')]; //todo: change this to only select children (right now it selects all in the doc)

    articleTextElements.forEach((articleTextElement, index) => {
      intersectionObserver.observe(articleTextElement);
      areElementsActive[index] = false;
    });
  });
</script>

<div class="scroller">
  <div class="background">
    {@render background()}
  </div>
  <div class="foreground">
    {#each articleTexts as articleText, index}
      <ArticleTextBox {articleText} />
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
</style>
