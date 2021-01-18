## 游戏规则
本贪吃蛇为多人对战，每回合玩家同时做出决策控制自己的n(n>=2)条蛇，与其他控制相同数量蛇的玩家对战。
玩家在n*m的网格中操纵n条蛇(蛇是一系列坐标构成的有限不重复有顺序的序列，序列中相邻坐标均相邻，即两坐标的x轴坐标或y轴坐标相同，序列中第一个坐标代表蛇头)，玩家只能控制蛇头的朝向(上、下、左和右)来控制蛇。蛇以恒定的速度前进(前进即为序列头插入蛇头指向方向下一格坐标，并删除序列末尾坐标)。蛇的初始位置为网格中的随机位置，初始长度为3格（可以更改）。每吃掉一个豆子长度加1。豆子数量可以指定，在游戏中豆子数量维持一个常数不变，即被吃掉则重新随机生成等数量的豆子。
蛇头在自己蛇的身体(即序列重复)、其他蛇的身体(即与其他序列有相同坐标)均判定为死亡。当输入了非法方向时(正在向左前进，无法选择向右)，随机选择一个合法方向。与传统贪吃蛇不同的是，蛇头超过边界时可以穿越到对称位置，不算做死亡。蛇死亡时可以按照初始化的设置重生，到达指定step数时游戏结束。
0表示没有对象 1 表示豆子，2 - n_player+1 表示玩家编号。

参数设置：蛇个数，食物数量，格子宽、高
食物：初始化随机生成指定数量的食物，位置不能与蛇身重叠；被吃掉后继续生成到指定数量
蛇：初始化蛇身长度为3，方向随机；蛇头超过格子宽、高后可穿越；碰到自身或其他蛇身则消失，重新生成
分数：吃掉一个食物加一分，触碰消失后清零
reward：吃到食物+1，触碰消失则扣掉（当前长度-初始化长度）的分数，其余情况为0
n_return: 每个玩家的n条蛇的累积得分

## 项目依赖
- `Pygame`
  - 版本至少为2.0, 使用命令`pip install pygame==2.0.0dev8`进行安装
- `Numpy`
- `PILLOW`
- `torch torchvision tensorboardX`
- `gym`

## 目录结构
```
|-- Competition_3v3snakes           // https://github.com/jidiai/Competition_3v3snakes.git
    |-- env		                    // 游戏环境
    |	|-- obs_interfaces		    // observation 观测类接口
	|	|	|-- observation.py		// 目前支持Grid
	|	|-- simulators		        // 模拟器
	|	|	|-- game.py
	|	|	|-- gridgame.py         // 网格类模拟器接口
	|	|-- config.ini		        // 相关配置文件
	|	|-- chooseenv.py 
	|	|-- snakes.py
	|-- examples
	|   |-- random
	|   |   |-- randomagent.py      // random策略
	|   |   |-- submission.py       // 示例提交文件
	|-- utils                       // 算法环境 主仓库工具包
	|-- run.py		                // 运行游戏	
```







