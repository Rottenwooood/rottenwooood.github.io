以下是学习江科大STM32教程的一些学习笔记，看完后会出一期完整文字版教程，改成易于阅读和学习的形式同步发在CSDN和bilibili上，敬请期待
---
11/30
### STM32F103C8T6规格

- 系列:主流系列STM32F1
- 内核:ARM Cortex-M3
- 主频:72MHz
- RAM:20K (SRAM)|
- ROM:64K (Flash)
- 供电:2.0~3.6V(标准3.3V)
- 封装:LQFP48

**片上资源/外设**
![图片](https://github.com/user-attachments/assets/eaf00c00-0d7f-4f01-bd39-3e20adceb884)
### 命名规则
![图片](https://github.com/user-attachments/assets/63081ca0-a835-413a-be15-4f7b907478c6)
### 系统结构
![图片](https://github.com/user-attachments/assets/f4405a48-9fe5-4f8e-9b98-cd8428ef0c4a)
### 引脚定义
蓝色：最小系统相关
红色：最小系统相关
加粗：常用

FT：引脚可容忍5V电压（但板子本身最高只输出3.3V）
![image-20241124211055250](https://github.com/user-attachments/assets/18ab6b45-fef5-4f67-8418-2d968239f0c6)
### 启动配置
![图片](https://github.com/user-attachments/assets/d889c986-5922-484f-9981-55d4d4255788)
- 最常用
- 串口下载用，系统存储器存储bootloader程序，其接收串口数据，刷新到主闪存中
- 用于程序调试
### 最小系统电路
![图片](https://github.com/user-attachments/assets/dcf17f84-01b5-4258-80aa-a169276b200a)
### 兼容
GigaDevice/MindMotion兼容STM32
### 型号分类及缩写
![图片](https://github.com/user-attachments/assets/525a2442-c2be-463e-a7fd-85f2e9963993)
### 新建工程步骤
- 建立工程文件夹，Keil中新建工程，选择型号
- 工程文件夹里建立Start、Library、User等文件夹，复制固件库里面的文件到工程文件夹
- 工程里对应建立Start、Library、User等同名称的分组，然后将文件夹内的文件添加到工程分组里
- 工程选项，C/C++，Include Paths内声明所有包含头文件的文件夹
- 工程选项，C/C++，Define内定义USE_STDPERIPH_DRIVER（使用库函数时）
- 工程选项，Debug，下拉列表选择对应调试器，Settings，Flash Download里勾选Reset and Run（STLINK）
### 基于寄存器开发
需要看着数据手册
### 基于库函数开发
需要随时去查看函数的声明，定义和说明
### 工程架构
![图片](https://github.com/user-attachments/assets/cc5cb2f0-d82d-41ca-828d-f9591e6a9bec)
Manage Project Items中选择三个文件夹中的文件

- Start：先添加md_s文件，然后添加其他.c.h文件
- Library：所有
- User：所有

### 工程选项

- C/C++
  - include paths,添加三个文件夹
  - define栏填写USE_STDPERIPH_DRIVER
- debug
  - 调试器选择ST-link
  - setting
    - flash download 
      - 选择reset and run
- main.c最后一行是空格