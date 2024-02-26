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
			<div class="hidden sm:block">
				<a href="/" class="btn btn-ghost normal-case text-xl">Day Care</a>
			</div>
			<div>
				<a class="self-auto" href="/login">Login</a>
			</div>
			<div class="dropdown dropdown-end mr-4">
				<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
				<!-- svelte-ignore a11y-label-has-associated-control -->
				<label class="btn btn-circle swap swap-rotate">
					<!-- this hidden checkbox controls the state -->
					<input type="checkbox" />

					<!-- hamburger icon -->
					<svg
						class="swap-off fill-current"
						xmlns="http://www.w3.org/2000/svg"
						width="32"
						height="32"
						viewBox="0 0 512 512"
						><path d="M64,384H448V341.33H64Zm0-106.67H448V234.67H64ZM64,128v42.67H448V128Z" /></svg
					>

					<!-- close icon -->
					<svg
						class="swap-on fill-current"
						xmlns="http://www.w3.org/2000/svg"
						width="32"
						height="32"
						viewBox="0 0 512 512"
						><polygon
							points="400 145.49 366.51 112 256 222.51 145.49 112 112 145.49 222.51 256 112 366.51 145.49 400 256 289.49 366.51 400 400 366.51 289.49 256 400 145.49"
						/></svg
					>
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
