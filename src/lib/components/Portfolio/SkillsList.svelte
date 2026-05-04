<!--
@component
SkillsList.svelte — Display skills grouped by category.
-->
<script>
  let { skills = [] } = $props();
</script>

<div class="skills-container">
  {#each skills as skillGroup (skillGroup.category)}
    <div class="skill-category">
      <h3>{skillGroup.category}</h3>
      <ul class="skill-items">
        {#each skillGroup.items as item (item)}
          <li>{item}</li>
        {/each}
      </ul>
    </div>
  {/each}
</div>

<style lang="scss">
  @use '$lib/styles' as *;

  .skills-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: var(--spacing-lg);
    margin: var(--spacing-lg) 0;
  }

  .skill-category {
    h3 {
      font-size: var(--font-size-md);
      margin-bottom: var(--spacing-sm);
      color: var(--color-text-primary);
    }
  }

  .skill-items {
    list-style: none;
    padding: 0;
    margin: 0;

    li {
      padding: var(--spacing-xs) 0;
      color: var(--color-text-secondary);
      font-size: var(--font-size-sm);

      &:before {
        content: '• ';
        color: var(--color-accent);
        margin-right: var(--spacing-xs);
      }
    }
  }
</style>
