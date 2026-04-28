<script>
  import Kicker from '$lib/components/Article/Kicker.svelte';
  import Headline from '$lib/components/Article/Headline.svelte';
  import Image from '$lib/components/Media/Image.svelte';
  import { base } from '$app/paths';

  let { data } = $props();
</script>

<div class="container">
  <Kicker text="{data.profile.name}'s Portfolio" href="{base}/" />
  <Headline text={data.clip.title} />

  <Image src={data.clip.image} alt={data.clip.title} />

  <p>{data.clip.description}</p>
</div>