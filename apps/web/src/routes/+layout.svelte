<script>
	import { getImageURL } from '$lib/utils.js';
	import '../app.postcss';
	export let data;

	import defaultAvatar from '$lib/assets/default-avatar.jpg';
</script>

<!--Buttons for user not logged in-->
{#if !data.user}
	<div class="min-h-full">
		<nav class="flex justify-between navbar ba-base-100 border-b">
			<div>
				<a href="/" class="btn btn-ghost normal-case text-xl">Day Care</a>
			</div>
			<div>
				<a class="self-auto" href="/login">Login</a>
			</div>
			<div class="dropdown dropdown-end mr-4">
				<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
				<!-- svelte-ignore a11y-label-has-associated-control -->
				<label tabindex="0" class="btn btn-primary btn-outline">Menu</label>
				<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
				<ul
					tabindex="0"
					class="menu menu-compact dropdown-content mt-3 p-2 shadow bg-base-100 rounded-box w-52"
				>
					<li>
						<a href="/my/orders" class="justify-between">My orders</a>
					</li>
					<li>
						<a href="/my/settings">Settings</a>
					</li>
					<li>
						<form action="/logout" method="POST">
							<button type="submit" class="w-full text-start">Logout</button>
						</form>
					</li>
				</ul>
			</div>
		</nav>
	</div>
{:else}
	<!--Buttons for loged in user-->
	<div class="min-h-full">
		<nav class="flex justify-between navbar ba-base-100 border-b">
			<div>
				{#if data.isAdmin}
					<a href="/" class="btn btn-ghost normal-case text-xl">Day Care Admin</a>
				{:else}
					<a href="/" class="btn btn-ghost normal-case text-xl">Day Care</a>
				{/if}
			</div>
			<div>
				<a class="self-auto" href="/login">Dashboard</a>
			</div>
			<div class="dropdown dropdown-end mr-4">
				<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
				<!-- svelte-ignore a11y-label-has-associated-control -->
				<label tabindex="0" class="btn btn-ghost btn-circle avatar">
					<div class="w-10 rounded-full">
						<img
							src={data.user?.avatar
								? getImageURL(data.user?.collectionId, data.user?.id, data.user?.avatar)
								: defaultAvatar}
							alt="user avatar"
						/>
					</div>
				</label>
				<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
				<ul
					tabindex="0"
					class="menu menu-compact dropdown-content mt-3 p-2 shadow bg-base-100 rounded-box w-52"
				>
					<li>
						<a href="/my/orders" class="justify-between">My orders</a>
					</li>
					<li>
						<a href="/my/settings">Settings</a>
					</li>
					<li>
						<form action="/logout" method="POST">
							<button type="submit" class="w-full text-start">Logout</button>
						</form>
					</li>
				</ul>
			</div>
		</nav>
	</div>
{/if}

<div class="py-4">
	<div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
		<slot />
	</div>
</div>
