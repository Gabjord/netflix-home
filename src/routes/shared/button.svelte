<script>
	export let type = 'primary'; // or 'secondary'
	export let flat = false;
	export let inverse = false;
</script>

<button
	class={` 
		shadow-xs 
		cursor-pointer 
		rounded-[6px] 
		px-[12px] 
		py-[8px] 
		font-bold 
		${flat ? 'shadow-none' : ''}

		${type === 'primary' && !inverse ? 'bg-[#d91b42] text-white' : ''}
		${type === 'secondary' && !inverse ? 'bg-[#45c496] text-white' : ''}

		${inverse && type === 'primary' ? 'border-[2px] border-red-500 bg-white text-[#d91b42]' : ''}
		${inverse && type === 'secondary' ? 'border-[2px] border-green-500 bg-white text-[#45c496]' : ''}
	`}
>
	<slot></slot>
</button>
