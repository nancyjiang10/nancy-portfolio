<!--
@component
Card.svelte — A card container with optional image, link, and footer actions.
-->
<script>
  import { asset } from '$app/paths';

  let { href = '', image = '', imageAlt = '', children, footer } = $props();

  // Resolve local images (those starting with /) using asset()
  // but not external URLs (http://, https://, //, data:)
  const resolvedImage = $derived(
    image && image.startsWith('/') && !image.startsWith('//')
      ? asset(image)
      : image
  );
</script>

{#snippet cardContent()}
  {#if image}
    <div class="card-image">
      <img src={resolvedImage} alt={imageAlt} />
    </div>
  {/if}
  <div class="card-body">
    {@render children()}
  </div>
  {#if footer}
    <div class="card-footer">
      {@render footer()}
    </div>
  {/if}
{/snippet}

{#if href}
  <a {href} class="card card-link">
    {@render cardContent()}
  </a>
{:else}
  <div class="card">
    {@render cardContent()}
  </div>
{/if}

<style lang="scss">
  .card {
    border: 1px solid var(--color-border, #ddd);
    border-radius: 4px;
    background: var(--color-white, #fff);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    height: 100%;
  }

  .card-link {
    display: flex;
    flex-direction: column;
    height: 100%;
    color: inherit;
    text-decoration: none;
    transition: box-shadow 0.2s ease;

    &:hover {
      box-shadow: 0 2px 8px var(--color-shadow, rgba(0, 0, 0, 0.12));
    }
  }

  .card-image {
    img {
      display: block;
      width: 100%;
      height: auto;
    }
  }
</style>
