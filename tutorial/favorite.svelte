<script>
    import AFButton from '/~/abfab/ui/button.svelte';
    
    let favorite = false;

    $: label = favorite ? 'Unfavorite' : 'Favorite';

    function toggleFavorite() {
        favorite = !favorite;
    }
</script>
<div>
    Is favorite: {favorite}
    <AFButton size="small" kind="primary" on:click={toggleFavorite}>{label}</AFButton>
</div>