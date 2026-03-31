<script>
	// @ts-ignore
	import Icon from '@iconify/svelte';
	// @ts-ignore
	let activeTab = $state('Cancel at any time');
	let tabs = $state([
		{ id: 1, tab: 'Cancel at any time', icon: 'mdi:clock-outline' },
		{ id: 2, tab: 'Watch anywhere', icon: 'mdi:cellphone' },
		{ id: 3, tab: 'Pick your price', icon: 'mdi:tag' }
	]);
</script>

<main class=" relative h-screen w-full">
	<!-- hero section -->
	<section
		class="flex h-screen w-full flex-col justify-evenly space-y-25 bg-[url(/background.jpg)] bg-cover bg-center bg-no-repeat"
	>
		<!-- header -->
		<header class="z-50 grid h-24 w-full grid-cols-3 items-center">
			<div></div>
			<div class=" justify-self-center">
				<img class="  w-26 lg:w-35" src="logo.png" alt="Netflix Logo" />
			</div>
			<div class=" justify-self-end pr-4">
				<button
					class=" h-fit w-fit cursor-pointer rounded-sm bg-red-600 px-3 py-2 font-medium text-white transition-all duration-500 ease-in hover:bg-white hover:text-red-500 md:px-5 md:font-semibold"
					>Sign In</button
				>
			</div>
		</header>

		<!-- hero -->
		<div class="z-50 flex-3 space-y-9 text-center text-white">
			<h2 class=" text-3xl font-semibold lg:text-6xl lg:font-bold">See what's next</h2>
			<p
				class="text-base font-medium uppercase md:text-xl md:font-semibold lg:text-2xl lg:font-bold"
			>
				Watch anywhere. Cancel Anytime
			</p>
			<button
				class="cursor-pointer rounded bg-red-600 px-6 py-2 text-xl font-semibold transition-all duration-500 ease-in hover:bg-white hover:text-red-500 lg:px-10 lg:py-3 lg:text-2xl"
				>Watch Free For 30 Days {'>'}
			</button>
		</div>
		<!-- overlay -->
		<div class="absolute inset-0 z-30 bg-black/80"></div>
	</section>
	<!-- tabs -->
	<div
		class="relative z-50 flex h-30 w-full list-none items-center justify-center gap-x-5 bg-black/90 p-4 text-gray-300/50 lg:gap-x-8"
	>
		{#each tabs as t}
			<button
				class={`flex w-20 flex-col items-center hover:text-white lg:w-60  ${activeTab.toLowerCase() === t.tab.toLowerCase() ? ' border-b-2 border-b-red-500 pb-5' : ''}`}
				onclick={() => (activeTab = t.tab)}
			>
				<Icon icon={t.icon} class=" h-10 w-35 md:h-13 md:w-40" />
				<span class=" block">{t.tab}</span>
			</button>
		{/each}
	</div>
	<!-- display tab contents -->
	<!-- first tab -->
	{#if activeTab.toLowerCase() === 'Cancel at any time'.toLowerCase()}
		<section class="w-full bg-black p-4 text-center text-balance text-white lg:grid lg:grid-cols-2">
			<div class="flex flex-col items-center justify-center gap-y-3">
				<p class="text-lg text-balance lg:text-2xl">
					If you decide Netflix isn't for you - no problem. No commitment. Cancel online anytime.
				</p>
				<button
					class=" sm w-fit cursor-pointer rounded bg-red-600 px-10 py-3 font-semibold transition-all duration-500 ease-in hover:bg-white hover:text-red-500"
					>Watch Free For 30 Days</button
				>
			</div>
			<div class="flex justify-center">
				<img src="tab-content-1.png" alt="img" class="w-96" />
			</div>
		</section>
		<!-- second tab -->
	{:else if activeTab.toLowerCase() === 'watch anywhere'.toLowerCase()}
		<section class="w-full bg-black pt-10 text-white">
			<div class="   space-y-2 px-6 pb-5">
				<p class="text-center text-xl text-wrap lg:text-2xl lg:text-nowrap">
					Watch TV shows and movies anytime, anywhere — personalized for you.
				</p>
				<!-- second tab button -->
				<div class="flex w-full justify-center">
					<button
						class="w-74 rounded-sm bg-red-600 px-2 py-3 transition-all duration-500 ease-in hover:bg-white hover:text-red-500"
						>WATCH FREE FOR 30 DAYS</button
					>
				</div>
			</div>

			<!-- img div -->
			<section class="mt-3 grid gap-3 pb-3 text-center lg:grid-cols-3 lg:text-left">
				<!-- 1 -->
				<div class="flex flex-col items-center gap-2">
					<img src="tab-content-2-1.png" alt="img1" class="w-full lg:w-103" />
					<h1 class="text-xl font-medium">Watch on your TV</h1>
					<p class="text-center text-balance text-gray-400/90">
						Smart TVs, PlayStation, Xbox, Chromecast, Apple TV, Blu-ray players and more.
					</p>
				</div>
				<!-- 2 -->
				<div class="flex flex-col items-center gap-2">
					<img src="tab-content-2-2.png" alt="img2" class="w-full lg:w-106" />
					<h1 class="text-xl font-medium">Watch instantly or download for later</h1>
					<p class="text-gray-400/90">Available on phone and tablet, wherever you go.</p>
				</div>
				<!-- 3 -->
				<div class="flex flex-col items-center gap-2">
					<img src="tab-content-2-3.png" alt="img3" class="w-full lg:w-106" />
					<h1 class="text-xl font-medium">Use any computer</h1>
					<p class="text-gray-400/90">Watch right on Netflix.com.</p>
				</div>
			</section>
		</section>
		<!-- third div -->
	{:else if activeTab.toLowerCase() === 'Pick your price'.toLowerCase()}
		<div class="w-full bg-black text-white">
			<h1 class="pt-3 text-center text-xl font-medium text-wrap lg:text-2xl lg:font-semibold">
				Choose one plan and watch everything on Netflix.
			</h1>
			<div class="w-full p-4">
				<!-- tab3 button -->
				<button class="mx-auto block w-fit rounded-sm bg-red-500 px-6 py-1"
					>Watch Free For 30 Days</button
				>
				<!-- table -->
				<section
					class="mx-auto mt-10 grid w-[80%] list-none grid-cols-[2fr_1fr_1fr] space-y-1 overflow-hidden pb-5 pl-8 font-semibold text-gray-300 lg:grid-cols-[2fr_1fr_1fr_1fr]"
				>
					<!-- table plans -->
					<div class=" text-base font-medium text-white uppercase lg:text-xl lg:font-semibold">
						feature
					</div>
					<div
						class="text-center text-base font-medium text-white uppercase lg:text-xl lg:font-semibold"
					>
						<p>Basic</p>
					</div>
					<div
						class="text-center text-base font-medium text-white uppercase lg:text-xl lg:font-semibold"
					>
						<p>Standard</p>
					</div>
					<div
						class="hidden text-center text-base font-medium text-white uppercase lg:block lg:text-xl lg:font-semibold"
					>
						<p>Premium</p>
					</div>
					<!-- 1 -->
					<li class="bg-gray-300/50 pt-1 pl-3">Monthly price after free month ends on 6/19/19</li>
					<li class="bg-gray-300/50 p-1 text-center uppercase">$8.99</li>
					<li class="bg-gray-300/50 p-1 text-center uppercase">$12.99</li>
					<li class=" hidden bg-gray-300/50 p-1 text-center uppercase lg:block">$15.99</li>

					<!-- 2 -->
					<li class="p-1 pl-3 uppercase">HD Available</li>
					<li class=" p-1 text-center uppercase">❌</li>
					<li class=" p-1 text-center uppercase">✅</li>
					<li class=" hidden p-1 text-center uppercase lg:block">✅</li>
					<!-- 3 -->
					<li class="bg-gray-300/50 p-1 pt-2 pl-3">Ultra HD Available</li>
					<li class="bg-gray-300/50 p-1 text-center uppercase">❌</li>
					<li class="bg-gray-300/50 p-1 text-center uppercase">❌</li>
					<li class="hidden bg-gray-300/50 p-1 text-center uppercase lg:block">✅</li>
					<!-- 4 -->
					<li class="p-1 pl-3">Screens you can watch on at the same time</li>
					<li class=" p-1 text-center uppercase">1</li>
					<li class=" p-1 text-center uppercase">2</li>
					<li class=" hidden p-1 text-center uppercase lg:block">4</li>
					<!-- 5 -->
					<li class="bg-gray-300/50 p-1 pt-2 pl-3">Watch on your laptop, TV, phone and tablet</li>
					<li class="bg-gray-300/50 p-1 text-center uppercase">✅</li>
					<li class="bg-gray-300/50 p-1 text-center uppercase">✅</li>
					<li class=" hidden bg-gray-300/50 p-1 text-center uppercase lg:block">✅</li>
					<!-- 6 -->
					<li class="p-1 pl-3">Unlimited movies and TV shows</li>
					<li class=" p-1 text-center uppercase">✅</li>
					<li class=" p-1 text-center uppercase">✅</li>
					<li class=" hidden p-1 text-center uppercase lg:block">✅</li>
					<!-- 7 -->
					<li class="bg-gray-300/50 p-1 pt-2 pl-3">Cancel anytime</li>
					<li class="bg-gray-300/50 p-1 text-center uppercase">✅</li>
					<li class="bg-gray-300/50 p-1 text-center uppercase">✅</li>
					<li class=" hidden bg-gray-300/50 p-1 text-center uppercase lg:block">✅</li>
					<!-- 8 -->
					<li class="p-1 pl-3">First month free</li>
					<li class=" p-1 text-center uppercase">✅</li>
					<li class=" p-1 text-center uppercase">✅</li>
					<li class=" hidden p-1 text-center uppercase lg:block">✅</li>
				</section>
			</div>
		</div>
	{/if}

	<!-- footer -->
	<footer class="mt-0.5 w-full bg-black text-base font-normal text-gray-400/90">
		<p
			class="mx-auto w-[80%] px-6 pt-3 pb-3 text-start transition-all duration-500 hover:text-white"
		>
			Questions? Call 1-866-579-7172
		</p>
		<section class="mx-auto grid w-[80%] grid-cols-2 px-6 lg:grid-cols-4">
			<!-- div1 -->
			<div class="list-none space-y-2 p-2 hover:text-white">
				<li>FAQ</li>
				<li>Investor Relations</li>
				<li>Ways To Watch</li>
				<li>Corporate Information</li>
				<li>Netflix Originals</li>
			</div>
			<!-- div2 -->
			<div class="list-none space-y-2 p-2 hover:text-white">
				<li>Help Center</li>
				<li>Jobs</li>
				<li>Terms Of Use</li>
				<li>Contact Us</li>
			</div>
			<!-- div3 -->
			<div class="list-none space-y-2 p-2 hover:text-white">
				<li>Account Speed</li>
				<li>Redeem Gift Cards</li>
				<li>Privacy</li>
				<li>Speed Test</li>
			</div>
			<!-- div4 -->
			<div class="list-none space-y-2 p-2 hover:text-white">
				<li>Media Centers</li>
				<li>Buy Gift Card</li>
				<li>Cookie Preferences</li>
				<li>Legal Notices</li>
			</div>
		</section>
	</footer>
</main>
