<script lang="ts">
  import { enhance } from '$app/forms';
  import { Combobox } from '@skeletonlabs/skeleton-svelte';

  interface ComboboxLanguage {
    label: string;
    value: string;
  }

  const comboboxLanguage: ComboboxLanguage[] = [
    { label: 'English', value: 'en' },
    { label: 'Russian', value: 'ru' },
    { label: 'Japanese', value: 'jp' }
  ];

  let selectedLanguage = $state(['en']);
</script>

<form method="POST" class="flex flex-1 flex-col gap-4" use:enhance>
  <div class="md:w-1/2">
    <Combobox
      data={comboboxLanguage}
      value={selectedLanguage}
      defaultValue={selectedLanguage}
      onValueChange={(e) => (selectedLanguage = e.value)}
      label="Select Language"
      placeholder="Language..."
    >
      {#snippet item(item)}
        <div class="flex w-full justify-between space-x-2">
          <span>{item.label}</span>
        </div>
      {/snippet}
    </Combobox>
    <input type="hidden" name="language" value={selectedLanguage} />
  </div>
  <div class="md:w-1/2">
    <Combobox
      data={comboboxLanguage}
      value={selectedLanguage}
      defaultValue={selectedLanguage}
      onValueChange={(e) => (selectedLanguage = e.value)}
      label="Select Language"
      placeholder="Language..."
    >
      {#snippet item(item)}
        <div class="flex w-full justify-between space-x-2">
          <span>{item.label}</span>
        </div>
      {/snippet}
    </Combobox>
    <input type="hidden" name="language" value={selectedLanguage} />
  </div>
  <div class="mt-4">
    <button type="submit" class="btn preset-filled">Apply</button>
  </div>
</form>
