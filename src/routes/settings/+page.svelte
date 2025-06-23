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

<form method="POST" class="flex flex-1 flex-col" use:enhance>
  <div class="grid grid-cols-1 gap-4 sm:grid-cols-3">
    <div>
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
    <div class="flex items-end justify-end sm:justify-start">
      <button type="submit" class="btn preset-filled">Apply</button>
    </div>
  </div>
</form>
