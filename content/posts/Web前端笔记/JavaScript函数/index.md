---
title: JavaScript函数
categories: ["Web前端笔记"]
date: 2026-03-25
---

其实逻辑大体没有问题，但是我可能会更喜欢从底层取了解这些概念，当然前端可能并不需要自己封装函数进行调用，或许是这样，不过从C转过来还是不是非常适应的，那我就从我的角度重新梳理一下知识点吧。

## 函数

### 函数封装

对于我来说调用是很简单的，但是，现在确实是让我对前端的看法越来要越明显，前端有的时候逻辑就是极其的不清晰，不封装可以直接调用，就算是外链一个库也不能直接用封装语句去写，让库去替你调用执行。

**封装目的**

如果说现在要去执行两步计算，输入三个个数字，前两个相加后的结果除第三的数字。四则运算确实可以很快解决，JavaScript也支持，我们就将其分成两步，假设不支持的情况，所以如果一个程序多次使用这样计算每次去写运算步骤肯定麻烦，所以这里就要用到**函数**这个概念。

**封装过程**

代码实现如下：

```javascript
// 输入三个数字
let a = 10;
let b = 20;
let c = 3;

// 第一步：前两个相加
let sum = a + b;

// 第二步：相加结果 除以 第三个数字
let result = sum / c;
```

这里先不管和浏览器的交互，简单的去看算法就行。当然使用`let result = (a + b) / c;`直接可以化繁为简，但是我只是想做一个多步骤的例子。所以如果不想每次将数据输入的时候都频繁这么写，就可以封装成函数的形式。

```javascript
// 封装成函数
function calculate(a, b, c) {
  let sum = a + b;
  let result = sum / c;
  return result;
}
```

### 函数调用

当然有了函数想要快速使用肯定是调用，所以直接将参数放入就行

```javascript
// 调用函数（直接用）
let final = calculate(10, 20, 3);
console.log(final);
```

这是后端函数常见的使用逻辑，但是前端不是。

## 案例

### 代码逻辑

在案例里面尤其突出，案例使用`p5.js`，直接外链就行

```text
https://cdn.jsdelivr.net/npm/p5@1/lib/p5.min.js
```

第一个最简单：

代码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		 <style>
			body {
				display: flex;
				justify-content: center;
				align-items: center;
				height: 100vh;
				margin: 0;
				background: #f0f0f0;
			}
		    </style>
	</head>
	<body>
		<script src="https://cdn.jsdelivr.net/npm/p5@1/lib/p5.min.js"></script>
		 <script>
		
		       
		        // p5.js setup函数 - 初始化
		        function setup() {
		            // 创建蓝色画布
		            createCanvas(800, 600);
		            background(0, 0, 255)
		            
		        }
		        
		        // p5.js draw函数 - 动画循环
		        function draw() {
		            //1. 绘制蓝色幕布
					 // 蓝色背景
					// 绘制背景（相当于清空画布）
		           
		            
		            // 绘制红色小球
		            fill(255, 0, 0); // 红色填充
		            noStroke(); // 无描边
		            circle(400, 300, 60); // p5的circle函数参数是直径
		            
					// fill(255,255,255)
					// circle(600,300,60);
		           
		        }
			</script>
	</body>
</html>
```




<iframe srcdoc="<!DOCTYPE html><html><head><meta charset=utf-8><style>body{display:flex;justify-content:center;align-items:center;height:100vh;margin:0;background:#f0f0f0;}</style></head><body><script src=https://cdn.jsdelivr.net/npm/p5@1/lib/p5.min.js></script><script>function setup(){createCanvas(800,600);background(0,0,255)}function draw(){fill(255,0,0);noStroke();circle(400,300,60)}</script></body></html>" width="840" height="640" style="border:none;"></iframe>


所以说这里没有任何调用，直接是写方法，调用直接交给`p5`这个库去做，也确实是没什么逻辑，调用本身就是应该在主程序执行的，这逻辑也是没谁了。其实还有更抽象的，估计后端的都理解，就是这玩意`draw()`函数是自己重复执行的，所以我特地写的`while()`和`do……while()`直接没作用，关键是我变量是直接放在函数内的，就是没料到这东西智能到会自己重复循环。但是说归说，还是要写东西的，所以先讲讲我对于最后一个思考的思路。

### 题解

触边，最简单就是定义x轴和y轴的变量，与初始画布的大小进行对比，如果大于等于边框，或者小于等于边框就就将移动变为反向。

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		 <style>
			body {
				display: flex;
				justify-content: center;
				align-items: center;
				height: 100vh;
				margin: 0;
				background: #f0f0f0;
			}
		    </style>
	</head>
	<body>
		<script src="https://cdn.jsdelivr.net/npm/p5@1/lib/p5.min.js"></script>
		 <script>
		
		       
		        // p5.js setup函数 - 初始化
		        function setup() {
		            // 创建蓝色画布
		            createCanvas(800, 600);
		            background("blue");
		        }
		        
                let runx = 10;
                let runy = 10;
                let ballx = 100;
                let bally = 100;
		        // p5.js draw函数 - 动画循环
		        function draw() {
		            // 绘制红色小球
                    background("blue");
		            fill(255, 0, 0); // 红色填充
		            noStroke(); // 无描边
		            circle(ballx, bally, 60); // p5的circle函数参数是直径
                    ballx = ballx + runx;
                    bally = bally + runy;

                    if(ballx >= 800 || ballx <= 0) {
                        runx = -runx;
                    }

                    if(bally >= 600 || bally <= 0) {
                        runy = -runy;
                    }
		        }
			</script>
	</body>
</html>
```

**但是**

问AI后还是有没看出来的问题，小球按照这个算法是中心点碰边，而半径3厘米没考虑进去，所以AI改成了

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		 <style>
			body {
				display: flex;
				justify-content: center;
				align-items: center;
				height: 100vh;
				margin: 0;
				background: #f0f0f0;
			}
		    </style>
	</head>
	<body>
		<script src="https://cdn.jsdelivr.net/npm/p5@1/lib/p5.min.js"></script>
		 <script>
		
		       
		        // p5.js setup函数 - 初始化
		        function setup() {
		            // 创建蓝色画布
		            createCanvas(800, 600);
		            background("blue");
		        }
		        
                let runx = 10;
                let runy = 10;
                let ballx = 100;
                let bally = 100;
		        // p5.js draw函数 - 动画循环
		        function draw() {
		            // 绘制红色小球
                    background("blue");
		            fill(255, 0, 0); // 红色填充
		            noStroke(); // 无描边
		            circle(ballx, bally, 60); // p5的circle函数参数是直径
                    ballx = ballx + runx;
                    bally = bally + runy;

                    if(ballx >= 800 - 30 || ballx <= 30) {
                        runx = -runx;
                    }

                    if(bally >= 600 - 30 || bally <= 30) {
                        runy = -runy;
                    }
		        }
			</script>
	</body>
</html>
```

我想了想这样不行啊，改了直径还是会出事，所以直接这样

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		 <style>
			body {
				display: flex;
				justify-content: center;
				align-items: center;
				height: 100vh;
				margin: 0;
				background: #f0f0f0;
			}
		    </style>
	</head>
	<body>
		<script src="https://cdn.jsdelivr.net/npm/p5@1/lib/p5.min.js"></script>
		 <script>
		
		       
		        // p5.js setup函数 - 初始化
		        function setup() {
		            // 创建蓝色画布
		            createCanvas(800, 600);
		            background("blue");
		        }
		        
                let runx = 10;
                let runy = 10;
                let ballx = 100;
                let bally = 100;
                let diameter = 60;
                let radius = diameter / 2;
		        // p5.js draw函数 - 动画循环
		        function draw() {
		            // 绘制红色小球
                    background("blue");
		            fill(255, 0, 0); // 红色填充
		            noStroke(); // 无描边
		            circle(ballx, bally, diameter); // p5的circle函数参数是直径
                    ballx = ballx + runx;
                    bally = bally + runy;

                    if(ballx >= 800 - radius || ballx <= radius) {
                        runx = -runx;
                    }

                    if(bally >= 600 - radius || bally <= radius) {
                        runy = -runy;
                    }
		        }
			</script>
	</body>
</html>
```

**效果**

<iframe srcdoc="<!DOCTYPE html><html><head><meta charset=utf-8><style>body{display:flex;justify-content:center;align-items:center;height:100vh;margin:0;background:#f0f0f0;}</style></head><body><script src=https://cdn.jsdelivr.net/npm/p5@1/lib/p5.min.js></script><script>let runx=10;let runy=10;let ballx=100;let bally=100;let diameter=60;let radius=diameter/2;function setup(){createCanvas(800,600);background(&quot;blue&quot;);}function draw(){background(&quot;blue&quot;);fill(255,0,0);noStroke();circle(ballx,bally,diameter);ballx=ballx+runx;bally=bally+runy;if(ballx>=800-radius||ballx<=radius){runx=-runx;}if(bally>=600-radius||bally<=radius){runy=-runy;}}</script></body></html>" width="840" height="640" style="border:none;"></iframe>



**还有这样一题**

<iframe srcdoc="<!DOCTYPE html><html lang=&quot;zh-CN&quot;><head><meta charset=&quot;UTF-8&quot;><title></title><script src=&quot;https://cdn.jsdelivr.net/npm/p5@1/lib/p5.min.js&quot;></script><style>body{display:flex;justify-content:center;align-items:center;min-height:100vh;margin:0;background:#f0f0f0;}</style></head><body><script>function setup(){createCanvas(800,600);background(255);}function draw(){background(255);stroke(0);noFill();circle(400,300,400);circle(320,220,150);fill(0);circle(290,220,80);noFill();circle(480,220,150);fill(0);circle(450,220,80);noFill();circle(400,320,40);circle(400,420,140);}</script></body></html>" width="840" height="640" style="border:none;"></iframe>

源码是这样的

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <title></title>
  <script src="https://cdn.jsdelivr.net/npm/p5@1/lib/p5.min.js"></script>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
      background: #f0f0f0;
    }
  </style>
</head>
<body>
  <script>
    function setup() {
      createCanvas(800, 600);
      background(255);
    }

    function draw() {
      background(255);

      stroke(0);
      noFill();
      circle(400, 300, 400);

      circle(320, 220, 150);
      fill(0);
      circle(290, 220, 80);

      noFill();
      circle(480, 220, 150);
      fill(0);
      circle(450, 220, 80);

      noFill();
      circle(400, 320, 40);

      circle(400, 420, 140);
    }
  </script>
</body>
</html>

```

