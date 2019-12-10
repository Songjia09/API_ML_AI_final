 |  表头   | 表头  |
 | -- | -- |
 |     名称 | 健康饮食APP |
 |  文件现状 | 进行中 |
 |  文件的主人 | 吉宋嘉 |
 |  领头的设计师 | 吉宋嘉 |
 |  领头的开发者 | 吉宋嘉 |
# PRD 价值主张设计 15%
![10479394-2e9e5a4f0e8241e8.png](https://upload-images.jianshu.io/upload_images/9457665-bf8d87a49b998163.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 客户细分：
- 客户任务列表：能够轻松了解每一餐是否是健康饮食，并且能够快速获取菜谱，又能分享自己的菜谱与他人交流。
- 痛点：平时做菜时没有热量对照，有时候摄入过多的热量导致了不健康的饮食；有时候做菜没用完全部食材，但又不想吃相同的菜品。
- 收益：可以轻松了解每一餐热量的摄入，节省了思考不同菜谱的时间。
### 价值地图：
- 产品和服务：菜品识别api、智能推荐。
- 痛点解决者：用菜品识别api对用户上传的菜品图片进行热量分析；通过智能推荐，为用户提供不同的菜谱课程和交流社区。
- 价值创造者：更方便的了解每一餐的热量，更快的寻找相似成分的菜谱。
# 加值宣言
通过调查发现，市面上有很多健身和做菜的APP，但将二者的优势结合者却甚微。而如今健康生活已经是主流，如何才能保证每一餐吃的健康，如何保证一家人摄入的热量达到标准？随着人工智能的发展，能够更方便的实现健康饮食。
- 使用百度ai中的菜品识别api，用户可以通过拍照上传来判断每一个菜品的热量，同时产品会提供一个参考量表告诉用户是否摄入过多或过少热量。
- 通过使用计算机视觉对图片进行分析，提取关键词例如：用户上传的照片中检测出“豆腐”的成分，可以像用户推荐豆腐相关的菜谱，同时通过阿里云api中的智能推荐像用户推荐相关的产品，如各种食材购买或者生活用品，如：锅、碗等电商的推荐。
## PRD2.核心价值 3%
解决用户对于健康饮食的追求提供热量计算，同时为用户提供轻松学习做菜的平台。
## PRD3.核心价值与用户痛点 3%
用户痛点宣言：
- 场景一：一名家庭主妇在家做菜，担心菜品热量过高让一家人吃的不健康，又不知道做什么菜好。
- 场景二：下班回家想点外卖，却又不能确认哪些菜太油太高热量。
- 场景三：正在减肥，想规划好每一餐，但是没法很清楚的知道饭菜卡路里。
## PRD4.人工智能概率性与用户痛点 3%
AI概率性考量：使用人工智能的加值的表述是否纳入判断有错的（如假阳False Positive假阴False Negative）的精确概率考量，以确保判错对用户体验的负面影响不会压过正面影响的机率。概率性参见 吴雪. 人工智能产品经理
## PRD5.需求列表与人工智能API加值 3%

需求列表：使用人工智能的加值是否反映到需求列表（核心功能的排序上）且PRD列出明显有可行及可用的API
# 原型 20%
## 原型1.交互及界面设计 5%
### 登陆界面：
![登录](https://images.gitee.com/uploads/images/2019/1210/221954_bb331c73_1532246.png "登录.png")
### 识别菜品界面：
![识别](https://images.gitee.com/uploads/images/2019/1210/222023_a50ab85c_1532246.png "识别.png")
### 社区模块：
![社区](https://images.gitee.com/uploads/images/2019/1210/222042_4e8d1e34_1532246.png "社区.png")
### “我的”模块：
![我](https://images.gitee.com/uploads/images/2019/1210/222013_04c55911_1532246.png "我.png")
### 菜谱模块：
![菜谱](https://images.gitee.com/uploads/images/2019/1210/222005_99e8a664_1532246.png "菜谱.png")
## 原型2.信息设计 5%
- APP热量识别的功能运用了菜品识别api功能，输入图片，输出文字，实现图文转换。
- 菜谱及其课程推荐运用了智能推荐功能，获取文字，输出图片及相关信息。
## 原型3.原型文档 5%
[原型文档](http://nfunm035.gitee.io/api/)
[原型下载](https://gitee.com/nfunm035/API)

## 原型4.口头操作说明 5%
很多人在吃饭的同时不仅仅想要美味，更想要健康同在。有了健康饮食APP的帮助，轻松快捷就能知道热量是否过多，又或者过少。本产品通过使用百度AI的菜品识别api和阿里云的智能推荐功能，为用户提供方便快捷的热量计算助手。只要随手一拍食物，即可知道热量，同时又能通过这些食物为用户提供感兴趣的菜谱。
# API 产品使用关键AI或机器学习之API的输出入展示 15%
## API1.使用水平 5%
使用水平：在PRD文件中是否有说明且展示，核心功能所应用的API之输入及输出
- 百度AI代码示例:
- 输请求代码示例：
```python
# encoding:utf-8

import requests
import base64

'''
菜品识别
'''

request_url = "https://aip.baidubce.com/rest/2.0/image-classify/v2/dish"
# 二进制方式打开图片文件
f = open('[本地文件]', 'rb')
img = base64.b64encode(f.read())

params = {"image":img,"top_num":5}
access_token = '[调用鉴权接口获取的token]'
request_url = request_url + "?access_token=" + access_token
headers = {'content-type': 'application/x-www-form-urlencoded'}
response = requests.post(request_url, data=params, headers=headers)
if response:
    print (response.json())
```
- 返回示例：
```python
HTTP/1.1 200 OK
x-bce-request-id: 73c4e74c-3101-4a00-bf44-fe246959c05e
Cache-Control: no-cache
Server: BWS
Date: Tue, 18 Oct 2016 02:21:01 GMT
Content-Type: application/json;charset=UTF-8
{
	"log_id": 7357081719365269362,
	"result_num": 5,
	"result": [
	{
		"calorie": "119",
		"has_calorie": true,
		"name": "酸汤鱼",
		"probability": "0.396031"
		"baike_info": {
			"baike_url": "http://baike.baidu.com/item/%E9%85%B8%E6%B1%A4%E9%B1%BC/1754055",
			"description": "酸汤鱼，是黔桂湘交界地区的一道侗族名菜，与侗族相邻的苗、水、瑶等少数民族也有相似菜肴，但其中以贵州侗族酸汤鱼最为有名，据考证此菜肴最早源于黎平县雷洞镇牙双一带。制作原料主要有鱼肉、酸汤、山仓子等香料。成菜后，略带酸味、幽香沁人、鲜嫩爽口开胃，是贵州“黔系”菜肴的代表作之一。这道菜通常先自制酸汤，之后将活鱼去掉内脏，入酸汤煮制。"
		}
	},
	{
		"calorie": "38",
		"has_calorie": true,
		"name": "原味黑鱼煲",
		"probability": "0.265432",

	},
	{
		"calorie": "144",
		"has_calorie": true,
		"name": "椒鱼片",
		"probability": "0.0998993"
	},
	{
		"calorie": "98",
		"has_calorie": true,
		"name": "酸菜鱼",
		"probability": "0.0701917"
	},
	{
		"calorie": "257.65",
		"has_calorie": true,
		"name": "柠檬鱼",
		"probability": "0.0471465"
	}]
}
```
## API2.使用比较分析 5%
### 百度AI菜品识别：
![百度](https://images.gitee.com/uploads/images/2019/1210/233002_00f34f6d_1532246.png "百度ai.png")
### 阿里云图像识别：
![阿里云](https://images.gitee.com/uploads/images/2019/1210/233833_9cec82ae_1532246.png "阿里云.png")
### 华为云图像识别：
![华为云](https://images.gitee.com/uploads/images/2019/1210/234506_81b21c66_1532246.png "华为云.png")
#### 百度与阿里云和华为云对比：
- 百度ai在菜品识别上可以提供置信度较高的答案，并且能够提供比较标准的热量参考。
- 百度ai只能够提供每一百克的热量，难以判断热量具体是多少。
- 阿里云和华为云的图像识别都只提供了图像打标的服务，并没有百度AI提供的热量参考，并不适合识别卡路里时使用。
### API3.使用后风险报告 5%
使用后风险报告：在PRD文件中是否有说明且提供连结证据，所使用的API类别的现在及未来发展性，如API市场竞争程度丶输入输出限制丶定价丶及可替代的程序库（改用自己开发的代码及数据库而不用API）等等
### API4.加分项 3%
使用复杂度：用了2个以上机器学习与人工智能的API之输入及输出
