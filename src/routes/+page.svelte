<script>
  import Profile from '$lib/components/Portfolio/Profile.svelte';
  import Hero from '$lib/components/Layout/Hero.svelte';
  import LandingGrid from '$lib/components/Layout/LandingGrid.svelte';
  import SkillsList from '$lib/components/Portfolio/SkillsList.svelte';

  let { data } = $props();
  const content = $derived(data.content);
</script>

<div>
  <Hero
    title={content.hero.title}
    subtitle={content.hero.subtitle}
    ctaText={content.hero.ctaText}
    ctaHref={content.hero.ctaHref}
    photo={content.profile.photo}
    photoAlt={content.profile.photoAlt}
  />

  <div class="container wide">
    <section class="featured">
      <h2>Featured</h2>
      <LandingGrid items={content.featured} />
    </section>

    {#if content.skills}
      <section class="skills">
        <h2>Skills</h2>
        <SkillsList skills={content.skills} />
      </section>
    {/if}
  </div>
</div>

<style lang="scss">
  .featured {
    margin-bottom: var(--spacing-xl);
  }

  .featured h2 {
    margin: var(--spacing-md) 0;
  }

  .skills {
    margin-bottom: var(--spacing-xl);
  }

  .skills h2 {
    margin: var(--spacing-md) 0;
  }
</style>