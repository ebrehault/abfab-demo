<script>
    import AFInput from '/~/abfab/ui/input.svelte';
    import AFRadio from '/~/abfab/ui/radio.svelte';
    import AFButton from '/~/abfab/ui/button.svelte';
    import { Content, navigateTo } from '/~/abfab/core.js';

	export let content;
    let {name, email} = content;
    
    async function save() {
        if (!email) return;
        if (!content.email) {
            await Content.create('/~/crud/contacts', email, {name, email});
        } else {
            await Content.update('', {name, email});
        }
        navigateTo(`/~/crud/list.svelte`);
    }
</script>
<svelte:head>
    <link rel="stylesheet" href="/~/abfab/pastanaga/pastanaga.css">
</svelte:head>
<main>
    <AFInput bind:value={name}
             label="Name"
             placeholder="Enter the contact name"
             required></AFInput>
    <AFInput bind:value={email}
             label="Email"
             placeholder="someone@mail.org"
             required></AFInput>
    <AFButton size="small" kind="primary" on:click={save}>Save</AFButton>
</main>
<style>
    main {
        padding: 1em;
    }
</style>