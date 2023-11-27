<script lang="ts">
	import weme1 from 'D:/Code/portfolioWEME/src/resources/pictures/weme1.jpg';
	import weme2 from 'D:/Code/portfolioWEME/src/resources/pictures/weme2.jpg';
	import weme3 from 'D:/Code/portfolioWEME/src/resources/pictures/weme3.jpg';
	import weme4 from 'D:/Code/portfolioWEME/src/resources/pictures/weme4.jpg';
	import weme5 from 'D:/Code/portfolioWEME/src/resources/pictures/weme5.jpg';
	import weme6 from 'D:/Code/portfolioWEME/src/resources/pictures/weme6.jpg';
	import weme7 from 'D:/Code/portfolioWEME/src/resources/pictures/weme7.jpg';
	import weme8 from 'D:/Code/portfolioWEME/src/resources/pictures/weme8.jpg';
	import weme9 from 'D:/Code/portfolioWEME/src/resources/pictures/weme9.jpg';
	import weme10 from 'D:/Code/portfolioWEME/src/resources/pictures/weme10.jpg';

	import MainImageContainer from './MainImageContainer.svelte';

	import { onMount } from 'svelte';

	let indexes: Array<number> = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

	let backLeftIndex: number;
	let backRightIndex: number;
	let leftIndex: number;
	let mainIndex: number;
	let rightIndex: number;

	const imageArray = [weme1, weme2, weme3, weme4, weme5, weme6, weme7, weme8, weme9, weme10];
	const lenghtArray = imageArray.length;
    
    function assignIndexes(){
        backLeftIndex = indexes[0];
		backRightIndex = indexes[1];
		leftIndex = indexes[2];
		mainIndex = indexes[3];
		rightIndex = indexes[4];
    }

	onMount(() => {
		assignIndexes()
	});

	function imgClicked(event: any) {
		var direction = event.detail.text;
		if (direction === 'right') {
			for (let index = 0; index < indexes.length; index++) {
				if (indexes[index] < lenghtArray - 1) {
					indexes[index] += 1;
				} else {
					indexes[index] = 0;
				}
			}
            console.log(indexes)
		}

		if (direction === 'left') {
			for (let index = 0; index < indexes.length; index++) {
				if (indexes[index] > 0) {
					indexes[index] -= 1;
				} else {
					indexes[index] = lenghtArray-1;
				}
			}
            console.log(indexes)
		}
		assignIndexes();
	}
</script>

<body>
	<div id="img" class="img-display">
		<div id="img-backleft" class="card card-backleft">
			<MainImageContainer
				src={imageArray[backRightIndex]}
				position="backleft"
				on:clicked={imgClicked}
			/>
		</div>

		<div id="img-backright" class="card card-backright">
			<MainImageContainer
				src={imageArray[backLeftIndex]}
				position="backleft"
				on:clicked={imgClicked}
			/>
		</div>

		<div id="img-left" class="card card-left">
			<MainImageContainer src={imageArray[leftIndex]} position="left" on:clicked={imgClicked} />
		</div>
		<div id="img-right" class="card card-right">
			<MainImageContainer src={imageArray[rightIndex]} position="right" on:clicked={imgClicked} />
		</div>
		<div id="img-main" class="card card-main">
			<MainImageContainer src={imageArray[mainIndex]} position="main" on:clicked={imgClicked} />
		</div>
	</div>
</body>

<style>
	.img-display {
		position: absolute;
		transform: translate(-25vh, -35vh);
	}
	.card {
		position: absolute;
	}
	.card-left {
		transform: translate(-40vh, -5vh);
	}
	.card-right {
		transform: translate(40vh, -5vh);
	}
	.card-backleft {
		transform: translate(-25vh, -12vh) scale(0.9);
	}
	.card-backright {
		transform: translate(25vh, -12vh) scale(0.9);
	}
	body {
		margin: 0px;
		background-color: grey;
		height: 100vh;
		display: grid;
		place-items: center;
	}
</style>
