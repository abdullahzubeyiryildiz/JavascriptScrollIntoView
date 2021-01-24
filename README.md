# Javascript ScrollIntoView Example

<br> <br>
#document.querySelector('.active').scrollIntoView({
<br> <br>
#behavior: 'smooth',   // Animasyonlu Scroll Yapması İçin
<br> <br>
#block: 'nearest', // Nearest En yakın Dikey hizalamayı tanımlar. Dikey Scroll etmesi için ('start','center','end','nearest') da mevcut
<br> <br>
inline : 'center' // Yatay hizalamayı tanımlar. ('start','center','end','nearest')
<br> <br>
});
 
<!DOCTYPE html>
<html lang="tr">
<head>
	<meta charset="utf-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, user-scalable=no initial-scale=1.0">

	<!-- Bootstrap CSS -->

	<title>Javascript Scroll View</title>
  
	<style>
		* {
			padding: 0;
			margin: 0;
			list-style: none;
			text-decoration: none;
			border: 0;
			outline: 0;
			box-sizing: border-box;
		} 
		nav {
			overflow-x: auto;
			padding: 0 20px;
			position: sticky;
			position: -webkit-sticky;
			top: 0;
			background-color: #fff;
		}	
		nav ul {
			display: flex;
			height: 60px;
			align-items: center;
		}
		nav ul li {
			padding-right: 20px;
		}
		nav ul li a {
			height: 30px;
			display: flex;
			align-items: center;
			padding: 0 30px;
			border-radius: 30px;
			background: #eee;
			color: #333;
			white-space: nowrap;
		}
		nav ul li.active a {
			background-color: lime;
		}
		#to-top {
			position: fixed;
			bottom: 20px;
			right: 20px;
		}
		section {
			height: 91vh;
			background: lime;
			margin-bottom: 20px;
			scroll-margin-top: 65px;
			padding: 10px;
		}
	</style>

</head>
<body>

	<a href="#" id="to-top">Yukarı Çık</a>

	<nav>
		<ul>
			<li class="active"><a href="#section1">Section 1</a></li>
			<li><a href="#section2">Section 2</a></li>
			<li><a href="#section3">Section 3</a></li>
			<li><a href="#section4">Section 4</a></li>
			<li><a href="#section5">Section 5</a></li>
		</ul>
	</nav>

	<section id="section1">Section 1</section>
	<section id="section2">Section 2</section>
	<section id="section3">Section 3</section>
	<section id="section4">Section 4</section>
	<section id="section5">Section 5</section>

	<script>
		const lists = document.querySelectorAll('nav ul li');

		lists.forEach(list => {
			list.addEventListener('click', (e) => {
				e.preventDefault();
				[...lists].map(list => list.classList.remove('active'));
				list.classList.add('active');
 					//console.log(list.querySelector('a').getAttribute('href'));
 					let target = list.querySelector('a').getAttribute('href').replace('#','');
 					document.getElementById(target).scrollIntoView({
 						behavior: 'smooth',
 						block: 'center',
 						inline : 'center'
 					});

 					var scrollTimeout;
 					addEventListener('scroll', () => {
 						clearTimeout(scrollTimeout);
 						scrollTimeout = setTimeout(() => {

 							document.querySelector('.active').scrollIntoView({
 								behavior: 'smooth',
 								block: 'nearest',
 								inline : 'center'
 							});


 						}, 100);
 					});

 					


 				});
		});


		document.getElementById('to-top').addEventListener('click', (e) => {
			e.preventDefault();
			document.body.scrollIntoView ({
				behavior: 'smooth', 
			});
		});
	</script>
</body>
</html>
