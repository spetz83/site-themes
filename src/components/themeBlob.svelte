<script lang="ts">
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';

  export let themeName: string;
  let textColor: any = writable('');
  let bgColor: any = writable('');
  export let themeSlug: string;

  onMount(() => {
    switch (themeSlug) {
      case 'pine-forest':
        textColor.set('#0a0302');
        bgColor.set('#03857f');
        break;
      case 'pine-forest-d':
        textColor.set('#03857f');
        bgColor.set('#0a0302');
        break;
      default:
        textColor = '';
        bgColor = '';
        break;
    }
  });

  let textColorVal = '';
  textColor.subscribe((value: string) => {
    textColorVal = value;
  });
  let bgColorVal = '';
  bgColor.subscribe((value: string) => {
    bgColorVal = value;
  });
</script>

<div class="border-2 rounded-2xl border-[#0a0302] bg-[#03857f] p-6">
  <h1>{themeName}</h1>
  <h2>Text Color: {textColorVal}</h2>
  <h3>Background Color: {bgColorVal}</h3>
</div>
