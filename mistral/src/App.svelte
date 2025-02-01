<script>



</script>

<body>
	<div id="hero">
		<div id="navbarcontainer">
			<ul id="listenavbar">
				<li><a href="#">Boutique</a></li>
				<li><a href="#">Caca</a></li>
			</ul>
		</div>
	</div>
</body>

<style>
	@font-face {
  font-family: 'Molend';
  src: url(../public/fonts/molendregular-mvd6p.ttf);
}


	#hero {
    background-image: url("/img/backgroundprinc.png");
    background-position: center;
	background-repeat: no-repeat;
    width: 100%;
    height: 100vh;
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