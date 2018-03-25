# HTML-Javascript-and-CSS-slideshow
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
	<meta name="viewport" content="width=device-width,initial-scale=1.0" />
	<meta http-equiv="X-UA-Compatible" content="ie=edge"/>
    <title></title>
	<style>	
	body,#slider,.wrap,.slide-content{
		margin:0;
		padding:0;
		font-family:Arial, Helvetica, sans-serif;
		width:100%;
		height:100vh;
		overflow-x:hidden;
	}
	.wrap{
		position:relative;
	}
	.slide{
		background-size:cover;
		background-position:center;
		background-repeat:no-repeat;
	}
	.slide1{
		background-image:url(Images/dj-720589_960_720.jpg);
		transition:5s;
	}
		.slide2 {
			background-image: url(Images/fireworks-879461_960_720.jpg);
			transition: 0.5s;
		}
		.slide3 {
			background-image: url(Images/hat-3075875_960_720.jpg);
			transition: 0.5s;
		}
	.slide-content{
		display:flex;
		flex-direction:column;
		justify-content:center;
		align-items:center;
		text-align:center;
	}
	.slide-content span{
		font-size:5rem;/*five times the default size*/
		color:white;
	}
	.arrow{
		cursor:pointer;
		position:absolute;
		top:50%;
		margin-top:-35px;
		width:0;
		height:0;
		border-style:solid;
	}
	#arrow-left{
		border-width:30px 40px 30px 0;
		left:0;
		margin-left:30px;
		border-color:transparent #fff transparent transparent;
	}
	#arrow-right
	{
		border-width:30px 0 30px 40px;
		border-color:transparent transparent transparent #fff;
		right:0;
		margin-right:30px;
	}
	</style>
</head>
<body>
	<div class="wrap">
		<div id="arrow-left" class="arrow">

		</div>
		<div id="slider">
			<div class="slide slide1">
				<div class="slide-content">
					<span>
						Image 1
					</span>
				</div>
			</div>
			<div class="slide slide2">
				<div class="slide-content">
					<span>
						Image 2
					</span>
				</div>
			</div>
			<div class="slide slide3">
				<div class="slide-content">
					<span>
						Image 3
					</span>
				</div>
			</div>
		</div>

		<div id="arrow-right" class="arrow">	</div>
	</div>
	<script>	
		//The querySelectorAll() method selects all element under the slide div
		var sliderImages = document.querySelectorAll('.slide');
		//The querySelector() method will select a specific id 
		var arrowRight = document.querySelector('#arrow-right');
		var arrowLeft = document.querySelector('#arrow-left');
		//This counter will be used to increment or decrement the value that the current slide has.It will be used in the slideLeft and slideRight functions
		var current = 0;
		//This will clear all images from the slide div
		function reset() {
			for (var i = 0; i < sliderImages.length; i++) {
				sliderImages[i].style.display = 'none';
			}
		};
		//This initializes the slider to display an image
		function startSlide() {
			reset();
			sliderImages[0].style.display = 'block';
		};
		//This will slide the slideshow to the image on the left
		function slideLeft() {
			reset();
			sliderImages[current - 1].style.display = 'block';
			current--;
		};
		//This will slide the slideshow to the image on the right
		function slideRight() {
			reset();
			sliderImages[current + 1].style.display = 'block';
			current++;
		};
		//The eventListner will listen for any clicks applied on the left arrow
		arrowLeft.addEventListener('click', function () {
			if (current === 0) {
				current = sliderImages.length;
			}
			slideLeft();
		});
		//The eventListner will listen for any clicks applied on the right arrow
		arrowRight.addEventListener('click', function () {
			if (current === sliderImages.length - 1) {
				current = -1;
			}
			slideRight();
		});
		startSlide();
	</script>
</body>
</html>
