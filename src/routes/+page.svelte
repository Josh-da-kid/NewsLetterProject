<script lang="ts">
	import { goto } from '$app/navigation';
	import { form } from '$lib/variable.svelte';

	let errorMessage = '';

	function validateEmail(e: any) {
		e.preventDefault();

		const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

		if (emailPattern.test(form.email)) {
			errorMessage = '';
			goto('/successPage');
		} else {
			errorMessage = 'Valid email required';
		}
	}

	function clearError() {
		errorMessage = '';
	}
</script>

<main>
	<div
		class="mx-auto items-center justify-center bg-white text-black lg:mt-22 lg:flex lg:w-fit lg:gap-12 lg:rounded-3xl lg:border lg:border-gray-300 lg:p-6 lg:shadow-lg"
	>
		<img
			src="/undraw_newsletter_q7fx.svg"
			alt="newsletter"
			class="mx-auto flex h-[400px] w-full items-center justify-center rounded-b-3xl bg-orange-600 lg:hidden"
		/>

		<div class="mt-6 p-4">
			<h1 class="text-3xl font-bold">Stay updated!</h1>
			<h3 class="mt-4 w-[350px] sm:w-[400px]">
				Join 60,000+ project managers receiving monthly updates on:
			</h3>

			<ul class="mt-4 max-w-[1000px] space-y-2">
				<div class="flex gap-2">
					<i
						class="fa-solid fa-check h-6 w-6 items-center justify-center rounded-full bg-red-500 p-1 text-white"
					></i>
					<p>Product discovery and building what matters</p>
				</div>

				<div class="flex gap-2">
					<i
						class="fa-solid fa-check h-6 w-6 items-center justify-center rounded-full bg-red-500 p-1 text-white"
					></i>
					<p>Measuring to ensure updates are a success</p>
				</div>

				<div class="flex gap-2">
					<i
						class="fa-solid fa-check h-6 w-6 items-center justify-center rounded-full bg-red-500 p-1 text-white"
					></i>
					<p>Add much more</p>
				</div>
			</ul>

			<form action="submit">
				<div class="mt-6">
					<label for="email">
						<div class="flex justify-between">
							<p class="font-medium">Email Address</p>

							<p class="text-red-500">{errorMessage}</p>
						</div>
						<input
							on:focus={clearError}
							bind:value={form.email}
							type="email"
							name="email"
							id="email"
							placeholder="johndoe@gmail.com"
							class="mt-2 rounded-lg border border-gray-200 p-3 pl-4 lg:w-full lg:p-2 {errorMessage.length >
							0
								? 'border-red-500 bg-red-500/20'
								: 'bg-white'}"
						/>
					</label>
				</div>

				<button
					on:click={validateEmail}
					class="btn mt-6 rounded-lg bg-black p-6 text-white transition-transform hover:scale-105 hover:bg-black/80 lg:w-full lg:p-2"
					>Subscribe to monthly newsletter</button
				>
			</form>
		</div>

		<img
			src="/undraw_newsletter_q7fx.svg"
			alt="newsletter"
			class="hidden h-[400px] w-[300px] rounded-lg bg-orange-600 lg:flex"
		/>
	</div>
</main>
