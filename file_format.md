# DHM Tracking 文件格式

## 结果文件夹:
**traj_YYYYmmddHHMMSS**，其上级目录为`setting.data_dir`
> 该结果文件夹下，有以下文件
- 轨迹文件，记录粒子信息，每个轨迹一个文件
- 速度文件，记录平均速度，只有一个文件
- 速度分布文件，记录区间分布，x,y,z和综合，共4个文件
- z方向频度分布，只有一个文件
- z方向持续时间分布，只有一个文件

### 轨迹文件(多个):
> count_trajno.txt，count为该轨迹粒子个数，trajno为程序得出的轨迹序号
>
> 格式：tick x y z vx vy vz v theta
>
> 每一行代表一个粒子的信息
> 其中tick,   粒子出现时刻计数，第一张图的tick为1，第二张为2，以此类推
- x,      粒子x坐标
- y,      粒子y坐标
- z,      粒子z坐标
- vx,     x方向速度
- vy,     y方向速度
- vz,     z方向速度
- v,      速度
- theta,  转角
- xtumble, tumble x方向速度
- ytumble, tumble y方向速度
- ztumble, tumble z方向速度
- angle,  tumble 夹角
- point,  tumble 拐点类型，1-急转 2-慢转

### 轨迹的msd文件(多个):
> count_trajno_msd.txt，每个轨迹一个
>
> 每一行是step为行号的mean square displacement

### msd拟合文件(msd_fit.txt):
> 格式 msd_filename count a b r2
>
> 每一行代表一个msd文件的拟合结果
>
> 其中:
- msd_filename, 对应的msd文件名
- count, 参与拟合的点数
- a, 参数a
- b, 参数b
- r2, r平方，拟合优度

### 速度文件(velocity.txt):
> 格式: tfile vx vy vz v alpha beta
>
> 每一行代表一条轨迹的信息
>
> 其中:
- tfile,  轨迹对应的文件
- vx,     x方向平均速度
- vy,     y方向平均速度
- vz,     z方向平均速度
- v,      平均速度
- alpha,  alpha角度
- beta,   beta角度

### 轨道速度分布文件
- vx_ranges_trajectory.txt
- vy_ranges_trajectory.txt
- vz_ranges_trajectory.txt
- vv_ranges_trajectory.txt

> 分别是x,y,z和综合的速度分布，以vx_ranges_trajectory.txt为例
>
> 格式: begin end count
>
> 其中:
- begin,  每一个range的左边界
- end,    每一个range的右边界
- count,  每一个range中的轨迹数目

### 粒子速度分布文件
- vx_ranges_point.txt
- vy_ranges_point.txt
- vz_ranges_point.txt
- vv_ranges_point.txt

> 分别是x,y,z和综合的速度分布，以vx_ranges_point.txt为例,
>
> 格式: begin end count
>
> 其中:
- begin,  每一个range的左边界
- end,    每一个range的右边界
- count,  每一个range中的轨迹数目

### z方向频度分布文件(z_frequency.txt)
> 格式: begin end count probability
>
> 其中:
- begin,  每一个range的左边界
- end,    每一个range的右边界
- count,  每一个range中的粒子个数
- probability,  每一个range中的粒子出现概率

### z方向持续时间分布文件(z_duration.txt)
> 格式: begin end average stdev
>
> 其中:
- begin,   每一个range的左边界
- end,     每一个range的右边界
- average, 每一个range中的粒子持续时间的均值
- stdev,   每一个range中的粒子持续时间的标准差

### z方向上速度热图分布
- z_vv_heatmap.txt
- z_vz_heatmap.txt
- z_vxy_heatmap.txt
- z_theta_heatmap.txt

> 分别是vv, vz, vxy, theta 对z的热图分布
>
> 其中第一行是v， 第一列是z，每个格子的值是归一化之后的v累加

### z方向上速度列表(z_v.txt)
> 格式： z vx vy yz vv
>
>是每一个轨迹的四列数据写在一个文件里面
