<script>
	import { goto } from '$app/navigation';
	import { form } from '$lib/variable.svelte';
	let email = 'email';
</script>

<main>
	<div
		class="mx-auto hidden items-center justify-center bg-white p-6 text-black lg:mt-22 lg:flex lg:w-fit lg:rounded-3xl lg:border lg:border-gray-300 lg:p-10 lg:shadow-lg"
	>
		<div class="w-[300px]">
			<div class="flex h-10 w-10 items-center justify-center rounded-full bg-red-500">
				<i class="fa-solid fa-check text-sm text-white"></i>
			</div>

			<h1 class="mt-4 text-4xl font-bold">Thanks for subscribing!</h1>
			<p class="mt-6">
				A confirmation email has been sent to <span class="font-bold"
					>{form.email ? form.email : email}</span
				>. Please open it and click the button inside to confirm your subscription
			</p>

			<button
				on:click={() => {
					goto('/');
				}}
				class="btn mt-6 w-full rounded-lg bg-black text-white transition-transform hover:scale-105 hover:bg-black/80"
				>Dismiss Message</button
			>
		</div>
	</div>
</main>

<!-- mobile -->
<div class="flex min-h-screen flex-col justify-between px-4 py-6 lg:hidden">
	<div class="w-[300px]">
		<div class="flex h-10 w-10 items-center justify-center rounded-full bg-red-500">
			<i class="fa-solid fa-check text-sm text-white"></i>
		</div>

		<h1 class="mt-4 text-4xl font-bold">Thanks for subscribing!</h1>
		<p class="mt-6">
			A confirmation email has been sent to <span class="font-bold"
				>{form.email ? form.email : email}</span
			>. Please open it and click the button inside to confirm your subscription
		</p>
	</div>

	<!-- Bottom button -->
	<a href="/"
		><button
			class="btn mt-6 w-full rounded-lg bg-black p-6 text-white transition-transform hover:scale-105 hover:bg-black/80"
		>
			Dismiss Message
		</button></a
	>
</div>
