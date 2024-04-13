<script>
	// @ts-nocheck
	/** @type {import('./$types').PageData} */
	export let data;
	import '../app.pcss';
	import { onMount } from 'svelte';
	import { returnRandomEmoji } from '$lib/randomEmoji';

	let count = 0;
	let finalText = '';

	// conter function
	function counter(intervel, max, step) {
		let interval = setInterval(() => {
			count = count + step > max ? max : count + step;
			finalText = count.toString() + ' ' + returnRandomEmoji();
			if (count >= max) {
				clearInterval(interval);
			}
		}, intervel);
	}

	const installcmd = ". <(curl -Ls https://bit.ly/udroid-installer)"

	onMount(() => {
		counter(10, data.count.count, 8);
	});
</script>

<div class="h-screen">
	<div class="flex flex-col h-[90%] items-center justify-center rounded-sm">
		<div class="p-6 rounded-xl">
            <a
			href="https://github.com/RandomCoderOrg/ubuntu-on-android"
			target="_blank"
			referrerpolicy="no-referrer"
			class="scroll-m-20 text-4xl font-extrabold tracking-tight lg:text-5xl"
			>UDROID Downloads</a
		>
		<p class="transition-all mt-4 font-light text-center font-mono text-3xl text-[#070704] dark:text-[#ededde]">{finalText}</p>
        </div>

		<blockquote class="mt-6 border-l-2 pl-6 italic text-[#070704] dark:text-[#ededde]">
		  Install udroid 
			<code
			  class="relative rounded bg-muted px-[0.3rem] py-[0.2rem] w-60 font-mono text-sm font-semibold"
			>
			  {installcmd}
			</code>
		</blockquote>
	</div>
	<footer class="text-center w-full leading-7 [&:not(:first-child)]:mt-6 text-sm">
		<a href="https://github.com/RandomCoderOrg/ubuntu-on-android/" target="_blank" rel="noopener noreferrer">RandomCoderOrg/ubuntu-on-android</a>
	</footer>
</div>
