<!-- 
Author:  Visalakshmi Chemudupati  
Date: 12 September,2023
Credits:
1. https://learn.svelte.dev/tutorial/dom-events
2. https://learn.svelte.dev/tutorial/motion
3. https://codesandbox.io/s/zy009?file=/Draggable.svelte
4. https://svelte.dev/repl/7d674cc78a3a44beb2c5a9381c7eb1a9?version=4.2.0
5. Online Documentation on Svelte, CSS, and HTML
-->


<script>
	let xPos = 0;
	let yPos = 0;
	let moving = false;
	
	function startMove(){	
		moving = true;
	}

	function stopMove(){
		moving = false;
	}

	function onMouseMove(evt){
		if(moving){
			xPos += evt.movementX;
			yPos += evt.movementY;
		}
	}
</script>

<!-- Element for the page -->
<div role="complementary" class="page">
	x is {xPos}, y is {yPos}
</div>

<!-- Element for the box -->
<section 
	role = "button"
	tabindex={0}
	on:mousedown={startMove}	
	on:mousemove={onMouseMove}
	style="left:{xPos}px; top:{yPos}px;" 
	class="draggable">
</section>

<!--Event Listener  -->
<svelte:window on:mouseup={stopMove} on:mousemove={onMouseMove}/>

<!--CSS -->
<style>
	.draggable{
		user-select: none;
		position: absolute;
		cursor: move;
		width: 50px;
		height: 50px;
		background-color: black;		
	}
	.page{
		height: 100%;
		width: 100%;
		padding-top: 4em;	
	}
</style>
