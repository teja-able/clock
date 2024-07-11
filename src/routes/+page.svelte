<script>
	import { onMount } from "svelte";
  
	let secondAngle = 0;
	let minuteAngle = 0;
	let hourAngle = 0;
  
	function updateClock() {
	  const now = new Date();
	  const seconds = now.getSeconds();
	  const minutes = now.getMinutes();
	  const hours = now.getHours();
  
	  secondAngle = seconds * 6;
	  minuteAngle = minutes * 6 + seconds * 0.1;
	  hourAngle = hours * 30 + minutes * 0.5;
	}
  
	onMount(() => {
	  updateClock();
	  const interval = setInterval(updateClock, 1000);
	  return () => clearInterval(interval);
	});
  </script>

<div class="bg-slate-500 p-10 h-[280px] w-[280px]">
	<div
		class="bg-red-500 outer-circle border-2 border-black h-48 w-48 rounded-full flex items-center justify-center relative"
	>
		
		<div
			class="text absolute text-white top-1/2 right-[25px] transform -translate-y-1/2 translate-x-full"
		>
			3
		</div>
		
		<div class="text absolute text-white bottom-1 left-1/2 transform -translate-x-1/2">6</div>
	
		<div
			class="text absolute text-white top-1/2 left-[25px] transform -translate-y-1/2 -translate-x-full"
		>
			9
		</div>

		<div class="text absolute text-white top-1 left-1/2 transform -translate-x-1/2">12</div>
		<!-- innerCircleWhite -->
		<!-- <div class="bg-white inner-circle border-2 border-black h-32 w-32 rounded-full flex items-center justify-center relative">
			<div class="h-5 w-5  rounded-full bg-pink-600 flex items-center justify-center"></div>
			<div class="clock-sec  h-[60px] rounded-[50px] w-[2px] border border-black bg-black origin-bottom animate-spin"></div>
		 <div class="clock-sec absolute h-[60px] rounded-[50px] w-[2px] border border-black bg-black origin-bottom "></div>
            <div class="clock-min absolute h-[56px] rounded-[50px] w-[4px] border border-black bg-black origin-bottom"></div>
            <div class="clock-hour absolute h-[50px] rounded-[50px] w-[6px] border border-black bg-black origin-bottom" ></div>
		</div> -->
		<div class="bg-white border-2 border-black h-32 w-32 rounded-full flex justify-center">
		     <div class="h-5 w-5 rounded-full bg-yellow-400 absolute top-[85px] left-[85px] z-10 "></div>
			<div class="clock-sec h-[60px] w-[1px] border-2 border-red-500  origin-bottom relative left-[6px] top-[3px] inset-0 z-9 "
			style="transform: rotate({secondAngle}deg);"></div>
			<div class="clock-min h-[45px] w-[2px] border-2 border-black   origin-bottom relative top-[18px] inset-0 z-8 "
			style="transform: rotate({minuteAngle}deg);"></div>
			<div class="clock-hour h-[35px] w-[2px] border-2 border-black    origin-bottom relative top-[28px] left-[-3px] inset-0"
			style="transform: rotate({hourAngle}deg);"></div>
		</div>
		

	</div>
</div>
<!-- inset 0 in poin in 3 -->
<style>
	@keyframes rotateHand {
          from {
            transform: rotate(0deg);
          }
          to {
            transform: rotate(360deg);
          }
        }

	/* .clock-sec {
		animation: spin 60s linear infinite;
	}

	.clock-min {
   
		animation: spin 3600s linear infinite;
	}

	.clock-hour {

		animation: spin 43200s linear infinite;
	} */
</style>
