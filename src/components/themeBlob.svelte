<script lang="ts">
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';

  export let themeName: string;
  let textColor: any = writable('');
  let bgColor: any = writable('');
  let childBgColor: any = writable('');
  export let themeSlug: string;

  onMount(() => {
    switch (themeSlug) {
      case 'pine-forest':
        textColor.set('0a0302');
        childBgColor.set('03857f');
        bgColor.set('0a0302');
        break;
      case 'pine-forest-d':
        textColor.set('03857f');
        childBgColor.set('0a0302');
        bgColor.set('0a0302');
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
  let childBgColorVal = '';
  childBgColor.subscribe((value: string) => {
    childBgColorVal = value;
  });
</script>

<div class="bg-[#{bgColorVal}] w-full p-10 grid rounded-2xl col-span-2">
  <div
    class="border-2 rounded-2xl border-[#{textColorVal}] bg-[#{childBgColorVal}] p-16 text-[#{textColorVal}] "
  >
    <h1 class="text-xl font-bold">{themeName}</h1>
    <h2 class="text-6xl font-bold">{textColorVal}</h2>
    <hr class="border-[#{textColorVal}] border-2 mt-3" />
    <div class="border-l-4 border-[#{textColorVal}] mt-6 h-24 flex px-8">
      <h3 class="text-3xl font-bold">Background Color: {bgColorVal}</h3>
    </div>
    <p class="mt-3 text-lg font-semibold">
      When a man needs to prove to a woman that he's actually… When a man loves a woman… I will be a
      bigger and hairier mole than the one on your inner left thigh! Well, I hope you also carry a
      spare bowl of candy beans. Here he comes. Here comes John Wayne. I may have committed some
      light treason. Well excuse me, Judge Reinhold.
    </p>
  </div>
</div>
