<script>
  import SkillsList from '$lib/components/Portfolio/SkillsList.svelte';
</script>

<meta title="Portfolio / SkillsList" />

<div>
  <h1>SkillsList</h1>
  <p>Display skills grouped by category.</p>
</div>

<h2>Default</h2>

<SkillsList
  skills={[
    {
      category: 'Data Analysis',
      items: ['Python', 'HTML & CSS'],
    },
    {
      category: 'Reporting',
      items: ['Investigative reporting', 'Accountability journalism', 'Policy analysis', 'Data visualization'],
    },
    {
      category: 'Tools',
      items: ['Excel & Google Sheets', 'Adobe Creative Suite'],
    },
  ]}
/>
