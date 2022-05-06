<svelte:options tag="my-counter" />

<script>
	import '@vonage/vwc-icon-button';
	import { createEventDispatcher } from 'svelte';
	import { get_current_component } from 'svelte/internal';
	import ChatWidget from './ChatWidget.svelte';
	import '@vonage/vwc-fab'
export let count = 0;

const component = get_current_component();
const originalDispatch = createEventDispatcher();

const dispatch = (name, detail) => {
	console.log('dispatching');
	originalDispatch(name, detail);
	if (component != undefined) {
		console.log('component != undefined');
		component.dispatchEvent(new CustomEvent(name, { ...detail, composed: true }));
	}
}


function inc() {
	count++;
	console.log('increasing');
	dispatch('inc', {
		count: count
	});
}

function dec() {
	count--;
	dispatch('dec', {
		count: count
	});
}

</script>

<style>
	.main-container {
		display: flex;
		align-items: center;
	}

	span {
		width: 4rem;
		display: inline-block;
		text-align: center;
		font-size: 200%;
	}
</style>
<ChatWidget></ChatWidget>
