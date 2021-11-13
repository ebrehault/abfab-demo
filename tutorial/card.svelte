<script>
    import Favorite from './favorite.svelte';
    export let content;
</script>
<svelte:head>
    <link rel="stylesheet" href="/~/abfab/pastanaga/pastanaga.css">
</svelte:head>
<img src="./icon.svg" alt="Icon">
<dl>
    <dt>Firstname</dt>
    <dd>{content.firstname}</dd>
    <dt>Lastname</dt>
    <dd>{content.lastname}</dd>
    <dt>Email</dt>
    <dd>{content.email}</dd>
</dl>
<Favorite></Favorite>
<style>
    img {
        width: 50px;
    }
</style>