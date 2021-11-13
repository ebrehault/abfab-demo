<script>
    import {onMount} from 'svelte';
    import { Content } from '/~/abfab/core.js';
    import AFButton from '/~/abfab/ui/button.svelte';
    import { navigateTo } from '/~/abfab/core.js';
 
    let contacts = [];
    onMount(async () => {
        contacts = await Content.folderContents('/~/crud/contacts');
    })
    
    async function deleteContact(path) {
        await Content.delete(path);
        contacts = contacts.filter(c => c.path !== path);
    }
</script>
<svelte:head>
    <link rel="stylesheet" href="/~/abfab/pastanaga/pastanaga.css">
</svelte:head>
<div class="pa-table-grid" style="grid-template-columns: minmax(240px, 8fr) minmax(210px, 7fr) 100px;">
    <div class="pa-table-grid--head">
        <div class="pa-table-grid--row">
            <div class="pa-table-grid--header">
                Name
            </div>
            <div class="pa-table-grid--header">
                Email
            </div>
            <div class="pa-table-grid--header">
                <AFButton kind="primary" aspect="basic" icon="plus" size="small"
                          on:click={() => navigateTo('/~/crud/edit.svelte')}>Add</AFButton>
            </div>
        </div>
    </div>
    <div class="pa-table-grid--body">
        {#each contacts as contact}
        <div class="pa-table-grid--row">
            <div class="pa-table-grid--cell">
                {contact.data.name}
            </div>
            <div class="pa-table-grid--cell">
                {contact.data.email}
            </div>
            <div class="pa-table-grid--cell">
                <AFButton kind="primary" aspect="basic" icon="pencil" size="small"
                          on:click={() => navigateTo(contact.path)}>Save</AFButton>
                <AFButton kind="primary" aspect="basic" icon="trash" size="small"
                          on:click={() => deleteContact(contact.path)}>Delete</AFButton>
            </div>
        </div>
        {/each}
    </div>
</div>
