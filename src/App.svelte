<script>
  import Counter from './lib/Counter.svelte';
  import Scrolly from './lib/Scrolly.svelte';

  const articleTexts1 = [
    'Scrolly piece 1',
    'Scrolly piece 2',
    'Scrolly piece 3',
    'Scrolly piece 4'
  ];

  const articleTexts2 = [
    'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent dui lectus, hendrerit at mi at, volutpat euismod magna. Aliquam pharetra tristique purus, nec faucibus ipsum accumsan quis. Ut pharetra sodales ex, sit amet vehicula massa. Nunc venenatis dui eget nibh semper gravida. Nulla arcu tortor, laoreet vestibulum hendrerit a, blandit at turpis. Interdum et malesuada fames ac ante ipsum primis in faucibus. Mauris tincidunt malesuada sem quis vehicula. Sed at facilisis nunc. Vivamus condimentum erat id euismod aliquet. Duis cursus sodales ultrices. Integer viverra convallis lacus, eu cursus ante bibendum finibus.',
    'Proin vitae est et mi euismod mollis. Donec iaculis sem a tempus aliquam. Vivamus augue mauris, placerat et velit in, gravida tincidunt diam. Praesent ut bibendum justo. Sed venenatis diam at eros dapibus, quis mattis arcu finibus. Nullam rhoncus tempus euismod. Proin condimentum lacus arcu, quis commodo magna mattis sed. Duis nec risus molestie, semper ex eu, venenatis lorem.'
  ];
</script>

{#snippet sticky1()}
  <div>
    <img alt="kwk duck" src="./public/duck.png" />
  </div>
{/snippet}

{#snippet sticky2()}
  <div>
    <img alt="kwk logo" src="./public/kwk.png" />
  </div>
{/snippet}

{#snippet sticky3()}
  <Counter />
{/snippet}

<main>
  <Scrolly articleTexts={articleTexts1} background={sticky1} />
  <Scrolly articleTexts={articleTexts2} background={sticky2} />
  <Scrolly background={sticky3} />
</main>

<style>
</style>
