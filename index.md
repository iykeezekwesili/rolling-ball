<!DOCTYPE html>
<html>
<head>
<meta name="viewport" 
	content="width=device-width, initial-scale=1">
<title>Ping-Pong</title>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<style>
	#startPing{
		position: absolute;
		bottom: 10px;
		right: 10px;
	}
	
	.ball{
		position: absolute;
		width: 100px;
		height: 100px;
		border-radius: 50%;
		opacity: 0.8;
		transition: 1s;
	}
</style>
</head>

<body>
	<button type="button" id="startPing">Ping a ball (0)</button>
	
	<script type="text/javascript">
		let startPing = document.getElementById("startPing")
		let maxBall = 10
		let ballCount = 0
		
		startPing.addEventListener("click", function(e){
			if (ballCount == maxBall) return
			ballCount = (ballCount == 0) ? 1 : ++ballCount
			startPing.textContent = "Ping a ball ("+ ballCount +")"
			new PingPong().startPing() 
		})
		
		function dropBalls(){
			startPing.textContent = "Ping a ball ("+ ++ballCount +")"
			new PingPong().startPing() 
		}
		
		let PingPong = function(){
			let winX = $(window).width()
			let winY = $(window).height()
			let colors = ["red", "green", "blue", "yellow", "black"]
			let _this = this
			let ball = null
			let s = 0
			
			this.moveBall = function(){
				this.ball.css({
					'left':this.x(), 
					'top':this.y(), 
					//'background':this.color()
				})
				
				setTimeout(function(){
					_this.moveBall()
					_this.s = Math.round((Math.random() * 500)) + 500
				}, this.s)
			}
			
			this.x = function(){
				let x = Math.round(Math.random() * winX)
				x = (x > winX-this.ball.width()) ? winX-this.ball.width() : x
				return x
			}
			
			this.y = function(){
				let y = Math.round(Math.random() * winY)
				y = (y > winY-this.ball.width()) ? winY-this.ball.width() : y
				return y
			}
			
			this.color = function(){
				let i = Math.round(Math.random() * colors.length)
				return colors[i]
			}
			
			this.startPing = function(){
				this.newBall()
				this.moveBall()
			}
			
			this.newBall = function(){
				this.ball = $("<div></div>")
					.addClass("ball")
					.css({'background':this.color()})
					.click(removeball)
					.appendTo($('body'))
			}
		}
		
		function removeball(){
			$(this).hide()
			startPing.textContent = "Ping a ball ("+ --ballCount +")"
		}
		
		start()
		function start(){
			let interval = setInterval(function(){
				dropBalls()
				if ($(".ball").length >= maxBall) clearInterval(interval)
			}, 1000)
		}
	</script>
</body>
</html><!DOCTYPE html>
<html>
<head>
<meta name="viewport" 
	content="width=device-width, initial-scale=1">
<title>Ping-Pong</title>
<script src="web-plugins/jQuery-3.4.1.js"></script>
<style>
	#startPing{
		position: absolute;
		bottom: 10px;
		right: 10px;
	}
	
	.ball{
		position: absolute;
		width: 100px;
		height: 100px;
		border-radius: 50%;
		opacity: 0.8;
		transition: 1s;
	}
</style>
</head>

<body>
	<button type="button" id="startPing">Ping a ball (0)</button>
	
	<script type="text/javascript">
		let startPing = document.getElementById("startPing")
		let maxBall = 10
		let ballCount = 0
		
		startPing.addEventListener("click", function(e){
			if (ballCount == maxBall) return
			ballCount = (ballCount == 0) ? 1 : ++ballCount
			startPing.textContent = "Ping a ball ("+ ballCount +")"
			new PingPong().startPing() 
		})
		
		function dropBalls(){
			startPing.textContent = "Ping a ball ("+ ++ballCount +")"
			new PingPong().startPing() 
		}
		
		let PingPong = function(){
			let winX = $(window).width()
			let winY = $(window).height()
			let colors = ["red", "green", "blue", "yellow", "black"]
			let _this = this
			let ball = null
			let s = 0
			
			this.moveBall = function(){
				this.ball.css({
					'left':this.x(), 
					'top':this.y(), 
					//'background':this.color()
				})
				
				setTimeout(function(){
					_this.moveBall()
					_this.s = Math.round((Math.random() * 500)) + 500
				}, this.s)
			}
			
			this.x = function(){
				let x = Math.round(Math.random() * winX)
				x = (x > winX-this.ball.width()) ? winX-this.ball.width() : x
				return x
			}
			
			this.y = function(){
				let y = Math.round(Math.random() * winY)
				y = (y > winY-this.ball.width()) ? winY-this.ball.width() : y
				return y
			}
			
			this.color = function(){
				let i = Math.round(Math.random() * colors.length)
				return colors[i]
			}
			
			this.startPing = function(){
				this.newBall()
				this.moveBall()
			}
			
			this.newBall = function(){
				this.ball = $("<div></div>")
					.addClass("ball")
					.css({'background':this.color()})
					.click(removeball)
					.appendTo($('body'))
			}
		}
		
		function removeball(){
			$(this).hide()
			startPing.textContent = "Ping a ball ("+ --ballCount +")"
		}
		
		start()
		function start(){
			let interval = setInterval(function(){
				dropBalls()
				if ($(".ball").length >= maxBall) clearInterval(interval)
			}, 1000)
		}
	</script>
</body>
</html>
