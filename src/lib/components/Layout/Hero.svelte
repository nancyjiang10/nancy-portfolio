<script>
  import { base } from '$app/paths';
  import Image from '$lib/components/Media/Image.svelte';

  let { title = '', subtitle = '', ctaText = '', ctaHref = '/', photo = '', photoAlt = '' } = $props();
</script>

<section class="hero">
  <div class="hero-inner container">
    <div class="hero-copy">
      <h1>{title}</h1>
      {#if subtitle}
        <p class="subtitle">{subtitle}</p>
      {/if}

      {#if ctaText}
        <a class="cta" href={ctaHref.startsWith('http') ? ctaHref : `${base}${ctaHref}`}>
          {ctaText}
        </a>
      {/if}
    </div>

    {#if photo}
      <div class="hero-photo">
        <Image src={photo} alt={photoAlt} size="small" />
      </div>
    {/if}
  </div>
</section>

<style lang="scss">
  @use '$lib/styles' as *;

  .hero {
    padding: var(--spacing-xl) 0;
  }

  .hero-inner {
    display: grid;
    grid-template-columns: 1fr var(--max-width-image-small);
    gap: var(--spacing-lg);
    align-items: center;
    min-height: 40vh;
  }

  h1 {
    font-size: clamp(2.25rem, 6vw, 4rem);
    margin: 0 0 var(--spacing-sm);
  }

  .subtitle {
    margin: 0 0 var(--spacing-md);
    color: var(--color-text);
    max-width: 40rem;
  }

  .hero-photo {
    justify-self: end;
    width: var(--max-width-image-small);
  }

  .hero-photo :global(.image) {
    border-radius: var(--border-radius-sm);
    box-shadow: 0 6px 20px var(--color-shadow);
    aspect-ratio: 4 / 5;
    object-fit: cover;
  }

  @include mobile {
    .hero-inner {
      grid-template-columns: 1fr;
      text-align: left;
    }

    .hero-photo {
      justify-self: start;
      width: 160px;
      margin-top: var(--spacing-md);
    }
  }
</style>
