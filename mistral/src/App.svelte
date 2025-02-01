<script>
	let xpos = 0;
	let ypos = 0;
	let t = 0;
	let luminance = 0;

	let interCircle = setInterval(() => {
		xpos = Math.cos(t)*500;
		ypos = Math.sin(t)*300;
		luminance = Math.abs(Math.cos(10*t));
		t+=0.01;
	}, 100);

	let leftButton = "-5rem";
	let rightButton = "-5rem";

	const enteredDiv = (which)=>{
		console.log("MOUSE ENTER FUCK")
		if(which == "left"){
			leftButton = "0rem";
		}else{
			rightButton = "0rem";
		}
	}

	const handleMouse = (m)=>{
		if(!moveLeft && !moveRight){
			if(m.clientX < 15){
				enteredDiv("left");
			}else if(m.clientX > 1300){
				enteredDiv("right")
			}else if (m.clientX > 15 & m.clientX < 1300){
				leftButton = "-5rem";
				rightButton ="-5rem";
			}
		}else{
			leftButton = "-5rem";
			rightButton = "-5rem";
		}
	}

	let moveLeft = false;
	let moveRight = false;

	const onRectangleClick = (wh)=>{
		console.log("cliiick")
		if(wh == "left"){
			moveLeft = true;
		}else if(wh == "right"){
			moveRight = true;
		}else{
			moveLeft = false;
			moveRight = false;
		}
	}

</script>

<body>
	<div class="left_part" style="position:fixed; width:100vw; height: 100vh; left:{moveLeft ? "0vw" : "-100vw"}; top:0rem; background-color:red; transition:all .3s cubic-bezier(0.075, 0.82, 0.165, 1); display:flex; justify-content:center; align-items:center;">
		<iframe width="560" height="315" src="https://www.youtube.com/embed/-oEdK7IZCEI?si=0JmaZXFebepDHxau" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
	</div>
	<div class="right_part" style="position:fixed; width:100vw; height: 100vh; left:{moveRight ? "0vw" : "100vw"}; top:0rem; background-color:#875F9A; transition:all .3s cubic-bezier(0.075, 0.82, 0.165, 1); display:flex; justify-content:center; align-items:center;">
		<iframe src="https://player.twitch.tv/?video=2355951007&parent=www.example.com" frameborder="0" allowfullscreen="true" scrolling="no" height="378" width="620"></iframe>
	</div>

	<div id="hero" on:mousemove={handleMouse} style="left:{moveLeft ? "-100vw" : "0vw"}; transition: all .3s cubic-bezier(0.075, 0.82, 0.165, 1);">
		
		<button class="button_left" style="position:fixed; left:{leftButton}; top:0rem; width:5rem; height:100%; background-color:red; border:none;transition:all .15s cubic-bezier(.09,.81,.37,1.02);" on:click={()=>onRectangleClick("left")}>
			<p style="font-family: Molend; color:white; font-weight:800; font-size:4rem; transform:scale({leftButton == "-5rem" ? "0" : "1"}); transition: all .25s cubic-bezier(0.075, 0.82, 0.165, 1);">Youtube</p>
		</button>
		<button class="button_right" style="position:fixed; right:{rightButton}; top:0rem; width:5rem; height:100%; background-color:#875F9A; border:none;transition:all .15s cubic-bezier(.09,.81,.37,1.02);" on:click={()=>onRectangleClick("right")}>
			<p style="position:relative;font-family: Molend; text-align:right; color:white; right:15rem; font-weight:800; font-size:4rem; transform:scale({rightButton == "-5rem" ? "0" : "1"}); transition: all .25s cubic-bezier(0.075, 0.82, 0.165, 1);">Twitch</p>
		</button>
		
		<!-- <div style="position:absolute; width:25rem; height:25rem; opacity:{luminance}; border-radius:100%; background-color:white; left:calc(5rem + {xpos}px); top: calc(5rem + {ypos}px); opacity:0.5; filter:blur(75px);"></div> -->
		<div id="navbarcontainer" style="transition:all .25s ease-in-out; opacity:{(moveLeft || moveRight) ? "0" : "1"};">
			<ul id="listenavbar">
				<li><a href="#">Boutique</a></li>
				<li><a href="#">Calendrier</a></li>
				<li><a href="#">Podium</a></li>
			</ul>
		</div>
		<!-- <div class="left" style="position:absolute; left:0rem;top:0rem;width:5rem;height:100%; z-index:50;" on:mouseenter={enteredDiv("left")} on:mouseleave={()=>{leftButton = "-5rem"}}></div> -->
		<!-- <div class="right" style="position:absolute; right:0rem;top:0rem;width:5rem;height:100%; z-index:50;" on:mouseenter={enteredDiv("right")} on:mouseleave={()=>{rightButton="-5rem"}}></div> -->
		
	</div>
</body>

<style>
	@font-face {
  font-family: 'Molend';
  src: url(../public/fonts/molendregular-mvd6p.ttf) format("truetype");
}


	#hero {
    background-image: url("/img/backgroundprinc.png");
    background-position: center ;
	background-size: cover;
	background-repeat: no-repeat;
    width: 100%;
    height: 100%;
	user-select: none;
	border: none;
}
	#navbarcontainer {
    display: flex;
    justify-content: flex-end; 
    align-items: center;       
    height: 100vh;             
    width: 100%;       
	text-align: right;        
    
  }

  #listenavbar {
	padding-right: 100px;
	list-style-type: none;
	padding-top: 250px;
  }

  #listenavbar a {
	font-family: 'Molend';
	text-decoration: none;
	color: white;
	font-size: 45px;
	line-height: 90px;
	text-shadow: 5px 5px 10px rgb(243, 112, 19);
	transition: all .3s cubic-bezier(0.165, 0.84, 0.44, 1);
}

  #listenavbar li {
	transform: scale(1); 
	transform-origin: right;
    transition: all 0.3s cubic-bezier(0.165, 0.84, 0.44, 1);
  }


  #listenavbar li:hover {
	color: #2571a0;
	transform: scale(1.2); 
	cursor: pointer;
  }

  #listenavbar li:hover > a{
	color: #2571a0;
  }

</style>