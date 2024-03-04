# SuperCLUE-Industry
中文原生工业测评基准

## 1. 介绍
随着大模型突飞猛进的发展，该项技术向各行业、各领域的渗透已成不可逆转的趋势。工业领域，作为国家重点发展、建设的，关乎国民经济命脉的重点行业，

大模型在其中的应用与布局已然取得了一些成绩，比如其可以用于工业领域的故障分析、辅助流程控制、代码生成等多个环节。

大模型虽适于工业应用，但多针对通用场景，不足以应对工业特有的专业性。工业数据包含术语、参数、流程及规范，通用模型难覆盖。
工业场景中文模型评估已起步但缺乏多轮开放式问题基准，导致开发者在模型优化和评估时无明确标准，难判其工业适宜性。

为深化和丰富工业模型评估体系，我们推出SuperCLUE-Industry(SC-Industry)。SC-Industry通过通过基础能力和应用能力两大方向、

六大维度对大模型进行效果评估，并加入了智能体Agent能力的测评。设计结合国际标准和中文特需，旨在推动工业大模型技术进步与创新。

文章地址：https://www.cluebenchmarks.com/superclue_industry.html

项目地址：https://github.com/CLUEbenchmark/SuperCLUE-Industry

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Industry/blob/main/resources/img/industry.jpg"  width="100%" height="100%"></img>

## 2. SuperCLUE-Industry
### 2.1特点
#### 1.中文原生工业大模型综合能力评估

立足于为通用人工智能时代提供中文世界基础设施，文字输入或prompt提示词都是中文原生的；并充分考虑国内工业领域行业特点与应用场景，从国内各工业领域实际问题出发，致力于打造适合中国语义环境的工业测评指标。

#### 2.深入工业领域行业细节

在考察工业大模型对基础知识与技能的掌握与应用能力的同时，该测评体系深入行业具体应用实际，考察大模型在工业文档问答、工业数据分析以及充当工业智能体核心应用的综合能力，旨在全面地衡量工业大模型除知识库之外的具有实践意义的解决行业具体问题的应用能力。

#### 3.工业领域通用测评基准与可拓展性

SC-Industry旨在建立中文工业大模型测评的通用基准并逐步向各细分领域拓展。
如SuperCLUE目前已发布的汽车行业测评基准，此后会在诸如原材料、制造、加工等领域进一步完善指标体系。


### 2.2 评估方法与思路

参考SuperCLUE一贯的细粒度评估方式，构建专用测评集，每个维度进行细粒度的评估并可以提供详细的反馈信息。

#### 测评集构建

中文prompt构建流程：1.参考现有prompt--->2.中文prompt撰写--->3.测试--->4.修改并确定中文prompt
参考国际标准和当前已有工作，针对每一个维度构建专用的测评集。

#### 测评方法
评估流程：1.获得<中文prompt>-->2.依据评估标准-->3.使用评分规则-->4.进行细粒度打分
结合超级模型，在定义的指标体系里明确每一个维度的评估标准。结合评估流程、评估标准、评分规则，将文本输入送入超级模型进行评估，并获得每一个维度的评估结果。
进行评估与人类一致性分析，并报告一致性表现。

### 2.3 指标体系

#### 1. 基础能力

##### 1.1 工业常规问答
  从工业产品的设计、制造、技术规格，到操作维护、故障排除、以及安全标准等全阶段的信息交流和问题解答活动。
  - 例如：在自动化装配线上，机器人臂突然频繁出现定位不准确的问题，导致产品装配失败率升高。请提供一种检测和校正机器人臂定位精度的方法。
  - 
##### 1.2 工业理解计算

  通过对工业领域特有指标的深入理解和准确计算来优化生产流程，提高产品质量，降低成本，以及保障工业安全。
  - 例如：假设一个高压化学反应容器需承受1500kPa压力，材料允许应力为250MPa，工作应变0.002，弹性模量200GPa，预期疲劳寿命100,000次，容积500L。求最大工作压力下的安全系数评估可靠性。
  - 
##### 1.3 工业代码生成

  评估模型在工业代码生成领域的能力。
  - 例如：编写一个SQL查询语句以计算上个月每台机器的总工作时间。数据库中有一个名为machine_logs的表，该表有两个字段：machine_id（机器的唯一标识符）和timestamp（记录机器工作的时间戳），每条记录表示一台机器的一次工作开始（work_start）或停止（work_end）。
  - 
#### 2. 应用能力

##### 2.1 工业数据分析

基于二维表格类数据，如数组，大模型能分析数据并提供洞察。
- 例如：生产车间的数据实例列表。每个实例包含记录时间、温度和车间名称。请根据我提供的数据信息，回传2024年2月27日中午十二点到晚上六点的A车间的全部温度数据信息。
- 
##### 2.2 工业文档问答

基于工业类文档的问题，需要结合一个或多个文档内容来进行回答。问题的答案需要限定在文档范围内，如果返回没有相关信息，则说明文档中不存在指定内容。
- 例如：给定文档信息关于金属加工的流程，要求说明成形加工的操作步骤。
- 
##### 2.3 工业智能体Agent

考察模型能否在一定的工业环境中自主或半自主地执行任务，做出决策，并与其他系统进行交互来优化或辅助工业流程。
- 例如：结合可使用的多个API详细信息，螺丝生产流程中突发紧急情况的处理流程。
  
## 三、测评邀请
### 3.1 时间规划
报名：3月4日----3月11日
参测模型确认：3月11日
测评执行：3月6日--3月中旬
测评报告发布：3月中旬

### 3.2 测评流程

1. 邮件申请
2. 意向沟通
3. 参测确认与协议流程
4. 提供测评API接口或大模型
5. 获得测评报告
   
### 3.2 申请评测地址

邮件标题：SuperCLUE-Industry工业测评申请，发送到contact@superclue.ai
请使用单位邮箱，邮件内容包括：单位信息、文生视频大模型简介、联系人和所属部门、联系方式

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Industry/blob/main/resources/img/industry_group.jpeg"  width="30%" height="30%"></img>

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Industry/blob/main/resources/img/brightmart_s.jpeg"  width="30%" height="30%"></img>
