<script>
  import CardGrid from '$lib/components/Data/CardGrid.svelte';
  import Card from '$lib/components/Data/Card.svelte';
  import { base } from '$app/paths';

  let { items = [] } = $props();
</script>

<CardGrid>
  {#each items as item (item.title)}
    <Card href={`${base}/clips/${item.slug}`} image={item.image} imageAlt={item.imageAlt}>
      <h3>{item.title}</h3>
      <p>{item.description}</p>
    </Card>
  {/each}
</CardGrid>

<style lang="scss">
  /* styles are inherited from CardGrid/Card */
</style>
