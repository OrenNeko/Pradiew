<!-- Date: 2024-08-09 | Author: OrenNeko -->

# LLM-for-GUI-Testing

## 目录
- [Make LLM a Testing Expert: Bringing Human-like Interaction to Mobile GUI Testing via Functionality-aware Decisions, ICSE 2024](#make-llm-a-testing-expert-bringing-human-like-interaction-to-mobile-gui-testing-via-functionality-aware-decisions-icse-2024-availabel-gptdroid)
- [AppAgent: Multimodal Agents as Smartphone Users, CHI 2025](#appagent-multimodal-agents-as-smartphone-users-chi-2025-availabel-appagent)
- [Guardian: A Runtime Framework for LLM-Based UI Exploration, ISSTA 2024](#guardian-a-runtime-framework-for-llm-based-ui-exploration-issta-2024-availabel-guardian)
- [LLM-Guided Scenario-based GUI Testing, TSE](#llm-guided-scenario-based-gui-testing-tse-availabelscengen)
- [LLMDroid: Enhancing Automated Mobile App GUI Testing Coverage with Large Language Model Guidance, FSE 2025](#llmdroid-enhancing-automated-mobile-app-gui-testing-coverage-with-large-language-model-guidance-fse-2025-availabel-llmdroid)

## 内容

### Make LLM a Testing Expert: Bringing Human-like Interaction to Mobile GUI Testing via Functionality-aware Decisions, ICSE 2024, Availabel: [GPTDroid](https://github.com/testinging6/GPTDroid)

#### 作者单位
 
- 中国科学院软件研究所  
- 中国科学院大学  
- 德国慕尼黑工业大学  
- 滴滴出行科技有限公司

#### 研究动机

- 基于概率或模型的测试工具存在覆盖率低下的问题。
- 基于机器学习的测试工具面临数据不足、泛化性差的问题。

#### 核心挑战

- 大语言模型难以关注全局探索历史，决策时易陷入局部信息困境，影响测试覆盖率提升。
- 对于获取的GUI信息，大语言模型更关注低级语义，易忽略组件交互和操作背后的高级语义。

#### 主要贡献

- 首次将GUI测试问题转化为交互式问答问题。
- 实现了GPTDroid，基于功能记忆机制让大语言模型关注全部信息。
- 评估了GPTDroid的有效性，并发现了一些应用中的Bug。

#### 值得关注的细节

- 提出6种与大语言模型交互的语言模式，包括3类上下文信息和3类提问模式：
    - **上下文信息**：
        - 应用基本信息描述
        - 页面GUI信息
        - 组件GUI信息
    - **提问模式**：
        - 一般操作提问，返回：操作类型+组件
        - 输入文本提问，返回：组件+输入内容
        - 无效行为的反馈，输入：当前不存在某个组件
- 提出1种功能记忆模式（function memory），帮助大语言模型关注历史探索信息，采用反馈提问方式，向大语言模型确认功能是否已测试完毕。基于功能（function/functionality）的记忆信息包括：
    - 已探索功能点
    - 覆盖的Activity
    - 近期测试操作


### AppAgent: Multimodal Agents as Smartphone Users, CHI 2025, Availabel: [AppAgent](https://github.com/TencentQQGYLab/AppAgent)

#### 作者单位

- 腾讯

#### 研究动机

- 现有的大语言模型测试智能体忽略了视觉上的信息，这影响了智能体对环境的感知能力和做出合理交互的能力。

#### 核心挑战

- 创建一个操作智能手机的智能体需要大量的训练数据；
- 不同应用程序的界面和操作逻辑各异，泛化性存在问题；

#### 主要贡献

- 开源了一个多模态的智能体操作框架AppAgent；
- 提出了一种创新的探索策略；
- 通过实验评估了AppAgent的有效性。

#### 值得关注的细节

- 探索阶段：智能体通过与应用进行交互，得到应用功能和操作反馈的文档记录，这一文档在后续交互中会被利用和进一步更新。除此之外，还采用观看人类演示来理解程序功能，相比于智能体交互，减少了出现错误和无效操作。

- 部署阶段：针对给出的具体任务，智能体通过观察和思考，考虑每一步的操作流程，并留下相关的记录，用于后续执行参考使用。

### Guardian: A Runtime Framework for LLM-Based UI Exploration, ISSTA 2024, Availabel: [Guardian](https://github.com/PKU-ASE-RISE/Guardian)

#### 作者单位

- 北京大学
- 美国得克萨斯大学达拉斯分校

#### 研究动机

- 大语言模型缺乏用户界面探索的领域知识，难以制定有效的探索策略。具体表现为：
    - 存在重复操作
    - 难以记忆已探索信息和利用新信息
    - 难以处理多步的复杂任务
    - 可能会产生幻觉
    - 遵循多指令或细粒度指令的能力较差
- 基于DroidBot-GPT的设计思路，将一部分计算任务卸载到大语言模型交互之外，以减轻大语言模型的负担。

#### 核心挑战

- 大语言模型容易陷入重复操作的阻塞问题；
- 大语言模型难以利用新出现的信息来重新规划操作路径。

#### 主要贡献

- 发现大语言模型在GUI测试中存在策略不佳的问题；
- 提出Guardian，用于减轻大模型在规划和计算任务中的耗费；
- 实验评估了Guardian的有效性。

#### 值得关注的细节

- 在初步研究环节，分析了大语言模型对应用的理解能力，实验内容是从页面选择元素以完成一些低级的任务，结论：
    - 大语言模型可以较好地理解应用界面内容和完成相关任务；
    - 大语言模型难以很好地服从“不能选择之前操作过的元素”。
- 参照了以往研究工作中关注的几个策略问题：
    - Time Machine指出要避免探索循环；
    - Vet指出要避免探索陷阱；
    - Reflexion指出在探索失效时应当给出替代方案；
    - DroidBot-GPT指出应当避免重复的动作。
- 核心思想是生成一组操作空间，在每轮测试环节前基于已有信息进行规划，去除可能会引起阻塞的操作。
- 失败案例包括：层级信息不足；存在滚动元素；存在相似元素。

### LLM-Guided Scenario-based GUI Testing, TSE, Availabel:[SCENGEN](https://sites.google.com/view/scengen)

#### 作者单位

- 南京大学
- 德国慕尼黑工业大学
- 同济大学

#### 研究动机

- 基于录制回放严重依赖手动编写的测试脚本；
- 基于随机的测试方法会生成大量伪随机的操作；
- 基于模型和概率的测试方法存在功能理解不充分问题。

#### 核心挑战

- 现有方法难以生成连续且有效的操作，难以模拟真实的用户操作；
- 生成能够触发特定功能的输入存在挑战，例如隐藏功能的触发、需要领域知识的触发和存在时间依赖关系的触发；
- 代码覆盖率的评估体系不足以说明测试方法的有效性，更应该关注功能点；

#### 主要贡献

- 提出一种基于GUI理解的测试方法，结合计算机视觉和大语言模型，理解应用程序的GUI，辅助测试用例生成；
- 构建了一个包含10种常见测试场景的应用程序数据集。

#### 值得关注的细节

- SCENGEN的测试流程环节
    - 记忆：分为长时记忆（Long-term Memory）、工作记忆（Working Memory）和短期记忆（Short-term Memory），在不同层次的测试环节中进行迭代更新。
    - 观察：使用边缘检测提取图形组件；使用OCR提取文本信息。
    - 决策：主要分为逻辑决策和组件定位两个环节。其中，逻辑决策生成操作，组件定位寻找操作的组件。
    - 执行：使用ADB执行操作。
    - 结果检查：通过自我修正解决错误或无效的操作。
    - 反馈：包括实时验证、状态转换验证和任务完成验证。

### LLMDroid: Enhancing Automated Mobile App GUI Testing Coverage with Large Language Model Guidance, FSE 2025, Availabel: [LLMDroid]()

#### 作者单位

- 华中科技大学
- 莫纳什大学
- OPPO

#### 研究动机

- 基于随机/模型/概率的测试方法覆盖率低，如DroidBot [ICSE17], Stoat [FSE17]；
- 基于学习的方法容易陷入循环，如Humanoid[ASE19], Deep GUI[ASE21], DQT[ICSE24], FastBot[ASE22], Q-testing[ISSTA20]；
- 基于大语言模型的工作聚焦构建智能体，耗费高，如AUITestAgent, MobileGPT[MobiCom24], AutoDroid[MobiCom24], MM-Navigator[Microsoft], AppAgent[Tencent]。

#### 核心挑战

- 如何区分不同的页面状态
- 如何找到重要的页面进行测试
- 如何决定什么时刻更换探索策略

#### 主要贡献

- 提出了LLMDroid，包含自主探索+指导测试两个环节；
- LLMDroid有效降低了交互时的时间耗费开销。

#### 值得关注的细节

- 针对GUI测试的核心问题提出了不同的解决策略
    - UI状态的区分：引入相似度计算和阈值的方式，对页面簇进行归纳总结
    - 测试页面/组件的重要性排序：使用LLM提示词对功能进行总结，并排序得到重要性
    - 测试策略的转换：基于覆盖率增长阈值进行阶段转换
    - 目标页面的访问：页面跳转流图和路径求解算法

## 小结

当前的GUI测试工作已经从完成基本测试任务到细化/提升测试性能：

- 基本测试任务：将App交互转换为大语言模型的QA过程
- 提升和改进：
    - 覆盖率
    - 测试任务/功能点的理解
    - 阻塞操作
    - 时间延迟
    - 更多信息的理解