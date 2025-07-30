<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<title>Valentine Confession</title>
	<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400..900&family=DM+Serif+Display:ital@0;1&family=Dancing+Script:wght@400..700&family=Playfair+Display:ital,wght@0,400..900;1,400..900&family=Quicksand:wght@300..700&display=swap" rel="stylesheet">
	<style>
		* { box-sizing: border-box; }
		h1, p { font-family: "Quicksand"; font-optical-sizing: auto; }
		h1 { font-weight: 200; }
		body { margin: 0px; background-color: #fce4ec; }

		.instruction {
			position: absolute;
			font-size: 1.6rem;
			color: rgba(255, 0, 0, 0.554);
			top: 36%;
			left: 50%;
			transform: translate(-50%, -50%);
		}
		.container {
			position: relative;
			width: 100%;
			height: 100vh;
			overflow: hidden;
		}
		.heart {
			position: absolute;
			left: 50%;
			top: 50%;
			text-align: center;
			transform: translate(-50%, -50%);
			transition: transform 2s;
			z-index: 1;
			cursor: pointer;
		}
		.heart > img {
			width: 50px;
			height: auto;
			animation-name: beat;
			animation-duration: 2s;
			animation-timing-function: ease-in-out;
			animation-iteration-count: infinite;
			animation-play-state: running;
		}
		.message {
			padding: 25px;
			background-color: #eee;
			font-family: "Quicksand", serif;
			font-optical-sizing: auto;
			font-size: clamp(16px, 10vw, 17px);
			text-align: justify;
			line-height: 1.5em;
			width: 80%;
			max-width: 550px;
			height: 78%;
			position: absolute;
			left: 50%;
			top: 50%;
			transform: translate(-50%, -50%);
			z-index: 0;
			animation-name: openmsg;
			animation-duration: 2s;
			animation-timing-function: linear;
			animation-play-state: paused;
			animation-fill-mode: forwards;
			box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
			border-radius: 5px;
			overflow: scroll;
			scrollbar-width: none;
		}
		.message .sincere {
			text-align: left;
			font-family: "Cinzel", serif;
			font-size: 14px;
			line-height: 1.2em;
		}
		.message .sincere p { margin: 0; }

		@keyframes beat {
			0% { width: 50px; }
			25% { width: 58px; }
			30% { width: 50px; }
			50% { width: 45px; }
			60% { width: 50px; }
			75% { width: 58px; }
			100% { width: 50px; }
		}
		@keyframes openmsg {
			0% { height: 0px; padding: 0px 20px; }
			100% { height: 75%; padding: 20px 20px; }
		}
		@keyframes heartMove {
			0% { top: 50% }
			100% { top: 85%; transform: translate(-50%, 0); }
		}
		.openNor { animation-direction: normal; animation-play-state: running; }
		.closeNor { animation-direction: reverse; animation-play-state: running; }
		.no-anim { animation: none; }
		.closed { height: 0px; padding: 0px 20px; }
		.bottom { bottom: 5px; }
		.openHer {
			animation-name: heartMove;
			animation-duration: 2s;
			animation-timing-function: linear;
			animation-play-state: running;
			animation-fill-mode: forwards;
		}
		.closeHer {
			animation-name: heartMove;
			animation-duration: 2s;
			animation-timing-function: linear;
			animation-play-state: running;
			animation-direction: reverse;
			animation-fill-mode: forwards;
		}
		.beating > img {
			animation-name: beat;
			animation-duration: 2s;
			animation-timing-function: ease-in-out;
			animation-iteration-count: infinite;
			animation-play-state: running;
		}
		.openedHer {
			top: 85%;
			transform: translate(-50%, 0);
		}
	</style>
</head>
<body>
	<p class="instruction">Click the heart!</p>
	<div class="container">
		<label for="messageState">
			<div class="heart">
				<img src="https://upload.wikimedia.org/wikipedia/commons/4/42/Love_Heart_SVG.svg" />
			</div>
		</label>
		<input id="messageState" type="checkbox" style="display:none" />
		<div class="message closed no-anim">
			<h1 style="font-family: Cinzel, serif; font-size: 40px; letter-spacing: 1.2px;">Dear Ghian,</h1>
			<p>
				<span>
					&emsp; I've been keeping this po in for a while, but I think National Girlfriend Day is the perfect time to say it to you po. You’re the reason my days feel brighter. Every little moment with you means more than I can put into words. Your smile, your laughter, the way you make everything feel lighter it all makes my heart race in the best way possible. So, here it is… I like you, a lot. Maybe even love. 
				</span>
				<br><br>
				<span>
					&emsp; Would you be my girlfriend po? No matter your answer, I just wanted you to know how special you are to me. You’ve filled my heart with warmth in ways I never expected, and for that, I’m grateful. If you say yes, I promise to make every day feel like National Girlfriend Day for you. I’ll treasure you, make you smile, and remind you just how much you mean to me.
				</span>
			</p>
			<br>
			<div class="sincere">
				<p style="font-weight: bold;">With Love,</p>
				<p>Your Admirer @zzzz_zzzz2839</p>
			</div>
		</div>
	</div>

	<!-- ✅ jQuery CDN -->
	<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

	<!-- ✅ Main Script -->
	<script>
		$("#messageState").on("change", () => {
			$(".message").removeClass("openNor closeNor");
			if ($("#messageState").is(":checked")) {
				$(".message").removeClass("closed no-anim").addClass("openNor");
				$(".heart").removeClass("closeHer openedHer").addClass("openHer");
				$(".container").stop().animate({ "backgroundColor": "#f48fb1" }, 2000);
			} else {
				$(".message").removeClass("no-anim").addClass("closeNor");
				$(".heart").removeClass("openHer openedHer").addClass("closeHer");
				$(".container").stop().animate({ "backgroundColor": "#fce4ec" }, 2000);
			}
		});

		$(".message").on('animationend webkitAnimationEnd oanimationend MSAnimationEnd', () => {
			if ($(".message").hasClass("closeNor"))
				$(".message").addClass("closed");
			$(".message").removeClass("openNor closeNor").addClass("no-anim");
		});

		$(".heart").on('animationend webkitAnimationEnd oanimationend MSAnimationEnd', () => {
			if (!$(".heart").hasClass("closeHer"))
				$(".heart").addClass("openedHer beating");
			else
				$(".heart").addClass("no-anim").removeClass("beating");
			$(".heart").removeClass("openHer closeHer");
		});
	</script>
</body>
</html>
