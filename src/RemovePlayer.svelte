<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let player = {
        name: ""
    };

    const onSubmit = (e) => {
        e.preventDefault();
        dispatch("removeplayer", player);

        // Clear the form after dispatching
        player = {
            name: ""
        };
    };
</script>

<form on:submit={onSubmit} class="grid-3">
    <input type="text" placeholder="Player Name" bind:value={player.name} />
    <input type="submit" class="btn btn-primary" value="Remove Player" />
</form>