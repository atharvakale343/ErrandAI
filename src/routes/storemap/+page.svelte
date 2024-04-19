<script lang="ts">
	import { goto } from '$app/navigation';
	import { fade, fly, draw } from 'svelte/transition';
	import { quintOut, linear, elasticInOut } from 'svelte/easing';

	// The M command moves to a given x and y location.
	// The h command draws a horizontal line with a given dx.
	// The v command draws a vertical line with a given dy.
	// The l command draws a line with a given dx and dy.
	// By default the origin is the upper-left corner.
	// This assumes we have flipped to coordinate system
	// so the origin is in the lower-left.
	// const commands = 'M 2 5 v-4 h3 v3 h2 v-3 h3 v4 h-9 l 5 4 l 5 -4 h-1';
	const commands = 'M 95 0 v75 h85 v92 h-90 v17 h90 v95 h-10';
	// const commands = 'M 0 0 v10';
	const max = 256;

	let display1 = true;
	let display2 = true;
	let show = false;

	setTimeout(() => {
		display1 = true;
	}, 500);

	setTimeout(() => {
		display2 = true;
	}, 1000);

	setTimeout(() => {
		show = true;
	}, 100);
</script>

<div class="flex h-screen items-center justify-center">
	<div
		class="mx-auto relative flex h-[600px] w-[300px] flex-col justify-between rounded-[2.5rem] border-[14px] border-gray-800 bg-[#F5F6EA] dark:border-gray-800"
	>
		<div class="fade-in-element address-and-chat-box space-y-1">
			<div
				class="address flex flex-row items-center justify-between space-x-3 rounded-t-[1.5rem] border border-black bg-[#E6E5DC] px-2 pt-3 pb-2 shadow-md"
			>
				<div class="flex flex-row items-center space-x-3">
					<i class="fa fa-angle-down" aria-hidden="true"></i>
					<h2 class="text-xs">145 Commonwealth Ave</h2>
				</div>
				<div class="icons flex grow justify-end gap-x-2">
					<button class="rounded-full hover:bg-white">
						<svg
							class="size-8 rounded-full border border-black p-1"
							viewBox="0 0 24 24"
							fill="none"
							xmlns="http://www.w3.org/2000/svg"
						>
							<g id="SVGRepo_bgCarrier" stroke-width="0"></g>
							<g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
							<g id="SVGRepo_iconCarrier"
								><path
									fill-rule="evenodd"
									clip-rule="evenodd"
									d="M12 1.25C7.71983 1.25 4.25004 4.71979 4.25004 9V9.7041C4.25004 10.401 4.04375 11.0824 3.65717 11.6622L2.50856 13.3851C1.17547 15.3848 2.19318 18.1028 4.51177 18.7351C5.26738 18.9412 6.02937 19.1155 6.79578 19.2581L6.79768 19.2632C7.56667 21.3151 9.62198 22.75 12 22.75C14.378 22.75 16.4333 21.3151 17.2023 19.2632L17.2042 19.2581C17.9706 19.1155 18.7327 18.9412 19.4883 18.7351C21.8069 18.1028 22.8246 15.3848 21.4915 13.3851L20.3429 11.6622C19.9563 11.0824 19.75 10.401 19.75 9.7041V9C19.75 4.71979 16.2802 1.25 12 1.25ZM15.3764 19.537C13.1335 19.805 10.8664 19.8049 8.62349 19.5369C9.33444 20.5585 10.571 21.25 12 21.25C13.4289 21.25 14.6655 20.5585 15.3764 19.537ZM5.75004 9C5.75004 5.54822 8.54826 2.75 12 2.75C15.4518 2.75 18.25 5.54822 18.25 9V9.7041C18.25 10.6972 18.544 11.668 19.0948 12.4943L20.2434 14.2172C21.0086 15.3649 20.4245 16.925 19.0936 17.288C14.4494 18.5546 9.5507 18.5546 4.90644 17.288C3.57561 16.925 2.99147 15.3649 3.75664 14.2172L4.90524 12.4943C5.45609 11.668 5.75004 10.6972 5.75004 9.7041V9Z"
									fill="#1C274C"
								></path></g
							>
						</svg>
					</button>
					<button class="rounded-full hover:bg-white">
						<svg
							class="size-8 rounded-full border border-black p-1"
							viewBox="0 0 48 48"
							xmlns="http://www.w3.org/2000/svg"
							fill="#000000"
						>
							<g id="SVGRepo_bgCarrier" stroke-width="0"></g>
							<g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
							<g id="SVGRepo_iconCarrier">
								<path d="M0 0h48v48H0z" fill="none"></path>
								<g id="Shopicon"
									><path
										d="M31.278,25.525C34.144,23.332,36,19.887,36,16c0-6.627-5.373-12-12-12c-6.627,0-12,5.373-12,12 c0,3.887,1.856,7.332,4.722,9.525C9.84,28.531,5,35.665,5,44h38C43,35.665,38.16,28.531,31.278,25.525z M16,16c0-4.411,3.589-8,8-8 s8,3.589,8,8c0,4.411-3.589,8-8,8S16,20.411,16,16z M24,28c6.977,0,12.856,5.107,14.525,12H9.475C11.144,33.107,17.023,28,24,28z"
									></path></g
								>
							</g>
						</svg>
					</button>
				</div>
			</div>
			<div class="flex flex-row mx-2 space-x-1 pt-2 items-center">
				<svg class="size-8" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
					<g id="SVGRepo_bgCarrier" stroke-width="0"></g>
					<g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
					<g id="SVGRepo_iconCarrier"
						><path
							fill-rule="evenodd"
							clip-rule="evenodd"
							d="M4.87617 3.75H19.1238L21 8.86683V10.5C21 11.2516 20.7177 11.9465 20.25 12.4667V21H3.75V12.4667C3.28234 11.9465 3 11.2516 3 10.5V8.86683L4.87617 3.75ZM18.1875 13.3929C18.3807 13.3929 18.5688 13.3731 18.75 13.3355V19.5H15V15H9L9 19.5H5.25V13.3355C5.43122 13.3731 5.61926 13.3929 5.8125 13.3929C6.63629 13.3929 7.36559 13.0334 7.875 12.4667C8.38441 13.0334 9.11371 13.3929 9.9375 13.3929C10.7613 13.3929 11.4906 13.0334 12 12.4667C12.5094 13.0334 13.2387 13.3929 14.0625 13.3929C14.8863 13.3929 15.6156 13.0334 16.125 12.4667C16.6344 13.0334 17.3637 13.3929 18.1875 13.3929ZM10.5 19.5H13.5V16.5H10.5L10.5 19.5ZM19.5 9.75V10.5C19.5 11.2965 18.8856 11.8929 18.1875 11.8929C17.4894 11.8929 16.875 11.2965 16.875 10.5V9.75H19.5ZM19.1762 8.25L18.0762 5.25H5.92383L4.82383 8.25H19.1762ZM4.5 9.75V10.5C4.5 11.2965 5.11439 11.8929 5.8125 11.8929C6.51061 11.8929 7.125 11.2965 7.125 10.5V9.75H4.5ZM8.625 9.75V10.5C8.625 11.2965 9.23939 11.8929 9.9375 11.8929C10.6356 11.8929 11.25 11.2965 11.25 10.5V9.75H8.625ZM12.75 9.75V10.5C12.75 11.2965 13.3644 11.8929 14.0625 11.8929C14.7606 11.8929 15.375 11.2965 15.375 10.5V9.75H12.75Z"
							fill="#000000"
						></path></g
					>
				</svg>
				<h1>Stores Map</h1>
			</div>
			<div class="instore pt-4">
				<img src="/instore.png" alt="in-store" />
			</div>
		</div>

		<div
			class="nav-bar flex flex-row items-center justify-center rounded-b-[1.5rem] border border-black bg-[#E6E5DC] shadow-2xl"
		>
			<button
				on:click={() => goto('/')}
				class="flex w-1/3 flex-col items-center justify-center px-1 py-2 hover:rounded-bl-[1.5rem] hover:bg-slate-100"
			>
				<svg class="size-8" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
					<g id="SVGRepo_bgCarrier" stroke-width="0"></g>
					<g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
					<g id="SVGRepo_iconCarrier">
						<path
							d="M17 3.33782C15.5291 2.48697 13.8214 2 12 2C6.47715 2 2 6.47715 2 12C2 13.5997 2.37562 15.1116 3.04346 16.4525C3.22094 16.8088 3.28001 17.2161 3.17712 17.6006L2.58151 19.8267C2.32295 20.793 3.20701 21.677 4.17335 21.4185L6.39939 20.8229C6.78393 20.72 7.19121 20.7791 7.54753 20.9565C8.88837 21.6244 10.4003 22 12 22C17.5228 22 22 17.5228 22 12C22 10.1786 21.513 8.47087 20.6622 7"
							stroke="#713f12"
							stroke-width="1.5"
							stroke-linecap="round"
						></path>
						<path
							d="M8 12H8.009M11.991 12H12M15.991 12H16"
							stroke="#713f12"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
						></path>
					</g>
				</svg>
				<h1 class="text-xs font-semibold text-yellow-900">ErrandAI</h1>
			</button>
			<button
				on:click={() => goto('/storelocator')}
				class="flex w-1/3 flex-col items-center justify-center px-1 py-2 hover:bg-slate-100"
			>
				<svg class="size-8" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
					<g id="SVGRepo_bgCarrier" stroke-width="0"></g>
					<g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
					<g id="SVGRepo_iconCarrier"
						><path
							fill-rule="evenodd"
							clip-rule="evenodd"
							d="M4.87617 3.75H19.1238L21 8.86683V10.5C21 11.2516 20.7177 11.9465 20.25 12.4667V21H3.75V12.4667C3.28234 11.9465 3 11.2516 3 10.5V8.86683L4.87617 3.75ZM18.1875 13.3929C18.3807 13.3929 18.5688 13.3731 18.75 13.3355V19.5H15V15H9L9 19.5H5.25V13.3355C5.43122 13.3731 5.61926 13.3929 5.8125 13.3929C6.63629 13.3929 7.36559 13.0334 7.875 12.4667C8.38441 13.0334 9.11371 13.3929 9.9375 13.3929C10.7613 13.3929 11.4906 13.0334 12 12.4667C12.5094 13.0334 13.2387 13.3929 14.0625 13.3929C14.8863 13.3929 15.6156 13.0334 16.125 12.4667C16.6344 13.0334 17.3637 13.3929 18.1875 13.3929ZM10.5 19.5H13.5V16.5H10.5L10.5 19.5ZM19.5 9.75V10.5C19.5 11.2965 18.8856 11.8929 18.1875 11.8929C17.4894 11.8929 16.875 11.2965 16.875 10.5V9.75H19.5ZM19.1762 8.25L18.0762 5.25H5.92383L4.82383 8.25H19.1762ZM4.5 9.75V10.5C4.5 11.2965 5.11439 11.8929 5.8125 11.8929C6.51061 11.8929 7.125 11.2965 7.125 10.5V9.75H4.5ZM8.625 9.75V10.5C8.625 11.2965 9.23939 11.8929 9.9375 11.8929C10.6356 11.8929 11.25 11.2965 11.25 10.5V9.75H8.625ZM12.75 9.75V10.5C12.75 11.2965 13.3644 11.8929 14.0625 11.8929C14.7606 11.8929 15.375 11.2965 15.375 10.5V9.75H12.75Z"
							fill="#713f12"
						></path></g
					>
				</svg>
				<h1 class="text-xs font-semibold text-yellow-900">Store Locator</h1>
			</button>
			<button
				on:click={() => goto('/storemap')}
				class="flex w-1/3 flex-col items-center justify-center px-1 py-2 hover:rounded-br-[1.5rem] hover:bg-slate-100"
			>
				<svg class="size-8" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
					<g id="SVGRepo_bgCarrier" stroke-width="0"></g>
					<g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
					<g id="SVGRepo_iconCarrier"
						><path
							d="M12 6H12.01M9 20L3 17V4L5 5M9 20L15 17M9 20V14M15 17L21 20V7L19 6M15 17V14M15 6.2C15 7.96731 13.5 9.4 12 11C10.5 9.4 9 7.96731 9 6.2C9 4.43269 10.3431 3 12 3C13.6569 3 15 4.43269 15 6.2Z"
							stroke="#386F53"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
						></path></g
					>
				</svg>
				<h1 class="text-xs font-semibold text-green-800">Store Map</h1>
			</button>
		</div>

		{#if display1}
			<button
				on:click={() => goto('/storemap')}
				class="fade-in-element absolute scale-[0.3] top-20 -left-32 overflow-visible hover:-translate-y-1 cursor-pointer transition"
			>
				<img
					src="/tap-to-view.png"
					alt="logo"
					in:fly={{ duration: 200, x: 100, y: 0, opacity: 0.8 }}
				/>
			</button>
		{/if}
		{#if display1}
			<button
				on:click={() => goto('/storemap')}
				class="fade-in-element absolute w-fit top-[150px] right-[90px] hover:-translate-y-1 cursor-pointer transition"
			>
				<span class="relative flex size-4">
					<span
						class="animate-ping fade-in-element absolute inline-flex h-full w-full rounded-full bg-sky-500 opacity-75"
					></span>
					<span class="relative inline-flex rounded-full size-4 bg-sky-600"></span>
				</span>
			</button>
		{/if}
		{#if display1}
			<button
				on:click={() => goto('/storemap')}
				class="fade-in-element absolute w-fit top-[270px] right-[90px] hover:-translate-y-1 cursor-pointer transition"
			>
				<span class="relative flex size-4">
					<span
						class="animate-ping fade-in-element absolute inline-flex h-full w-full rounded-full bg-sky-500 opacity-75"
					></span>
					<span class="relative inline-flex rounded-full size-4 bg-sky-600"></span>
				</span>
			</button>
		{/if}
		{#if display1}
			<button
				on:click={() => goto('/storemap')}
				class="fade-in-element absolute w-fit top-[365px] right-[140px] hover:-translate-y-1 cursor-pointer transition"
			>
				<span class="relative flex size-4">
					<span
						class="animate-ping fade-in-element absolute inline-flex h-full w-full rounded-full bg-sky-500 opacity-75"
					></span>
					<span class="relative inline-flex rounded-full size-4 bg-sky-600"></span>
				</span>
			</button>
		{/if}
		{#if show}
			<button on:click={() => goto('/storemap')} class="fade-in-element absolute w-fit top-[125px] right-[5px]">
				<svg width={272.5} height={389} viewBox="0 0 {max} {max}">
					<g transform="translate(0 {max}) scale(1 -1)">
						<path
							transition:draw={{ duration: 3000 }}
							d={commands}
							fill="none"
							stroke="#0284c7"
							stroke-width="3px"
						/>
					</g>
				</svg>
			</button>
		{/if}
	</div>
</div>

<!-- https://play.tailwindcss.com/7w4XtxmIGc -->
