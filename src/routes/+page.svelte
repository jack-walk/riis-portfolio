<script>
  import Profile from '$lib/components/Portfolio/Profile.svelte';
  import Card from '$lib/components/Data/Card.svelte';
  import CardGrid from '$lib/components/Data/CardGrid.svelte';
  import { base } from '$app/paths';

  let { data } = $props();
  const content = $derived(data.content);
</script>

<div class="container wide">
  <Profile
    name={content.profile.name}
    tagline={content.profile.tagline}
    photo={content.profile.photo}
    photoAlt={content.profile.photoAlt}
    email={content.profile.email}
    github={content.profile.github}
    linkedin={content.profile.linkedin}
    bio={content.profile.bio}
  />

  <CardGrid>
    {#each content.clips as clip (clip.title)}
      <Card
        href="{base}/clips/{clip.slug}"
        image={clip.image}
        imageAlt={clip.title}
      >
        <h3>{clip.title}</h3>
        <p>{clip.description}</p>
      </Card>
    {/each}
  </CardGrid>

  <div class="page-divider" aria-hidden="true">
    <img src="{base}/photos/bunnies.png" alt="" />
  </div>
</div>

<style lang="scss">
  .page-divider {
    max-width: var(--max-width-wide);
    margin: var(--spacing-xl) auto 0;
    padding: 0 var(--spacing-md) var(--spacing-xl);
  }

  .page-divider img {
    display: block;
    width: 30%;
    height: auto;
    margin: 0 auto;
  }
</style>