<script>
	export let data;
	import heroImage from '$lib/assets/img/child_with_blocks.jpg';
</script>

{#if !data.user}
	<div class="hero rounded-xl" style="background-image: url({heroImage});">
		<div class="hero-overlay bg-opacity-70 rounded-xl" />
		<div class="hero-content text-center text-neutral-content">
			<div class="max-w-md">
				<h1 class="mb-5 text-5xl font-bold text-slate-100">Hello there</h1>
				<p class="py-6 text-slate-100">
					Welcome to Creative Kids Cottage, where every child's journey begins with love, laughter,
					and learning! Our nurturing environment is designed to spark curiosity, foster creativity,
					and provide a safe haven for your little ones to explore the wonders of the world.
				</p>
				<a href="/register">
					<button class="btn btn-primary">Get Started</button>
				</a>
			</div>
		</div>
	</div>
{:else}
	<div class="hero min-h-screen bg-base-200">
		<div class="hero-content text-center">
			<div class="max-w-md">
				<h1 class="mb-5 text-5xl font-bold">Hello there {data.user.name}</h1>
				<p class="mb-5">Click the get started button to update your profile.</p>
				<a href="/my/settings/profile">
					<button class="btn btn-primary">Get Started</button>
				</a>
			</div>
		</div>
	</div>
{/if}
