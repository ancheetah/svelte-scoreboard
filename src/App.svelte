<script>
    import Navbar from './Navbar.svelte';
    import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';
	import RemovePlayer from './RemovePlayer.svelte';

    let players = [
        {
            name: 'John Doe',
            points: 53
        },
        {
            name: 'Sam Smith',
            points: 45
        },
        {
            name: 'Sara Wilson',
            points: 34
        }
    ];
	
	const addPlayer = (e) => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	};

	const removePlayer = (e) => {
		const deletePlayer = e.detail;
		players = players.filter( player => {
			return player.name.toLowerCase() !== deletePlayer.name.toLowerCase() 
		});
	}
</script>

<header>
    <Navbar />
</header>
<main>
    <div class="container">

		<!-- Catch the dispatch from the AddPlayer component -->
		<AddPlayer on:addplayer={addPlayer}/> 
		<RemovePlayer on:removeplayer={removePlayer}/>

        {#if players.length === 0}
            <p>No Players</p>
        {:else}
            {#each players as player}
                <Player name={player.name} points={player.points} />
            {/each}
        {/if}
    </div>
</main>
