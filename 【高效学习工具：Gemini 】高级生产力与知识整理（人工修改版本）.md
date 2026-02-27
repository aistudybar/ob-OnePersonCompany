
## 零：Gemini简介
### 特点：多模态！超长Token！连接NLM！\[2]

![image.png](https://repo.in4tree.com/2026/02/14_1771138332862.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771138452481.png)


### 3种模式 \[2]

| **模式**       | **职场类比** | **适用场景**                     |
| ------------ | -------- | ---------------------------- |
| **Flash**    | 勤奋的实习生   | 简单查询、快速总结、翻译、处理格式化数据。        |
| **Pro**      | 高级主管     | 追求稳健、不出错。适合制定标准 SOP、项目排期。    |
| **Thinking** | 百万年薪顾问   | 具备逻辑推理链。适合处理利益博弈、复杂死局、跨维度分析。 |

**案例**：Thinking模式适合复杂逻辑推理！ \[3]

![image.png](https://repo.in4tree.com/2026/02/14_1771140338301.png)


## 一、 结合Google Gemini官方文档总结的三个使用技巧 \[1]


![image.png](https://repo.in4tree.com/2026/02/14_1771134305620.png)


### 1.1 系统提示词（个性化！）：系统指令 (System Instructions) 与 Gems

 > 注：可以让 AI 永久记住你的背景，避免输出“正确的废话”。


**新老两个版本Gem（新版是OPAL！）** \[2]

![image.png](https://repo.in4tree.com/2026/02/14_1771138845805.png)



- **设置路径**：
    
    - **Gemini**：首页左下角 `设置` -> `个人智能` -> `Gem 指令` \[3]
    - 
![image.png](https://repo.in4tree.com/2026/02/14_1771140118929.png)
- 
    - **Gemini 官网 (Gems)**：通过 `新增 Gem` 填入指令。这是一种提示词持久化技术 \[2]\[1]
    
    ![image.png](https://repo.in4tree.com/2026/02/14_1771059578441.png)
    ![image.png](https://repo.in4tree.com/2026/02/14_1771059649644.png)
    ![image.png](https://repo.in4tree.com/2026/02/14_1771136078538.png)
        
    - **Google AI Studio**：支持多套指令切换（如：代码模式、学术模式）\[1]

![image.png](https://repo.in4tree.com/2026/02/14_1771059371744.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771136114201.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771140285511.png)

        
- **提示词的示例** \[1]：
-  ![image.png](https://repo.in4tree.com/2026/02/14_1771059808586.png)
    
    - **用户画像**：AI 会基于此过滤掉不适用的建议。例如：设定硬件环境（如：Mac M2、Win11）、职业身份、甚至健康状况
    
    - **行为人设**：要求“禁止谄媚”、“直接指出错误”、“使用数据说话” \[2]\[1]
    
    - **实效性约束**：由于模型数据截断至 2025 年 1 月，必须强制指令：“涉及实时信息时必须开启 Google 搜索” \[1]


### 注：ChatGPT设置系统提示词\[1]

![image.png](https://repo.in4tree.com/2026/02/14_1771136217417.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771136272521.png)


### 1.2 禁忌事项 \[1]

![image.png](https://repo.in4tree.com/2026/02/14_1771136375028.png)

1. **禁改温度 (Temperature)**：官方强调！Gemini 3 靠高熵值进行逻辑路径探索，调低温度会破坏推理链！
    
2. **禁加“请一步步思考”**：模型已原生内置推理机制，额外指令会导致解析混乱！
    
3. **禁情绪勒索**：如“扮演我奶奶”等旧技巧已被识别为低质干扰，会导致 AI 拒绝回答！
    

### 1.3 规避幻觉与事实验证 \[1]

![image.png](https://repo.in4tree.com/2026/02/14_1771137090790.png)

**幻觉产生的根源**

- 大语言模型的生成机制决定了其倾向于“猜测“而非“承认无知”，Gemini3因具备更强的推测能力，在处理复杂问题时幻觉风险反而可能升高（Gemini3Pro幻觉率约为13.6%）。
	
 - 奖励机制缺陷：模型训练中“猜对“有分，“不答”零分，导致模型倾向于构建看似合理的错误答案。
	
- 顺从性偏误：模型倾向于顺从用户的预设前提。若用户在提问中包含错误假设，模型往往会基于该错误前提继续推理，而非反驳。


**规避策略**

1.系统级约束（Prompt Engineering）

- 在System Instructions中明确规定：遇到不确定的信息必须回答“查不到确切信息”。·要求模型对输出内容进行置信度评级（如：非常确定、需验证、推测）。
	
- 强制模型先验证前提：在回答前，先审查用户问题中的假设是否成立，要求 AI 在输出前检查是否违背了预设画像或实效性限制。

2.检索增强生成（RAG）与工具联动

- NotebookLM联动：利用Gemini3连通NotebookLM的能力，强制模型仅基于用户上传的私有资料库（如PDF文档）结合网络搜索进行回答，限制其自由发挥的空间。
	
- 上下文填充：利用Gemini3的长上下文窗口，直接投喂原始资料进行限定域问答。

3.交叉验证法（Cross-Verification）

- 多模型对抗：使用模型A生成内容，使用模型B进行校验。

【参考】Hallucination Leaderboard （模型的幻觉率排名）



---

## 二、 进阶功能

### 2.1 NotebookLM+Gems这个组合功能 \[3]

**NotebookLM来源**：上传海量文档

![image.png](https://repo.in4tree.com/2026/02/14_1771140682869.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771140704913.png)


**Gems AI助手**：私人行业顾问

![image.png](https://repo.in4tree.com/2026/02/14_1771140731377.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771140890794.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771140911125.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771140935447.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771140964609.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771140990109.png)


### 2.2 互联应用：Google 生态的深度集成 \[2]

![image.png](https://repo.in4tree.com/2026/02/14_1771138593096.png)

通过指令唤起 Google 生态，打通信息孤岛 \[2]\[3]：

- **@Gmail / @Drive**：直接搜索上周老板发的邮件，提取附件中的预算表，并基于此写 PPT 大纲。
    
- **NotebookLM 联动**：将 NotebookLM 作为外部智库。Gemini 可以调用其中的笔记资料，不仅减少幻觉，还能学习你的专业话术 \[2]\[3]
    


### 2.3 视觉化与引导式学习 \[2]

- **动态检视 (Dynamic View)**：将 Token 或上下文窗口等抽象概念生成为“互动式小程式”，边操作边理解（限付费版/Pro！）

**示例：什么是Token和上下文窗口？**

![image.png](https://repo.in4tree.com/2026/02/14_1771138022525.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771138108623.png)

生成一个互动式网页APP：

> 【灵感】快速生成网页APP比如用于文章或视频教程的素材（类似音频）！！增加了文章或视频的特色和竞争力！比如两个滑块与墙之间碰撞次数与圆周率直接的关系

![image.png](https://repo.in4tree.com/2026/02/14_1771138135062.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771138255524.png)


- **引导式学习**：上传大规模 Excel（如 20 万单元格）后，AI 会主动问你：“接下来想聚焦在哪个维度？”，而非单纯丢出总结。
    

![image.png](https://repo.in4tree.com/2026/02/14_1771138673589.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771138698103.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771138743894.png)




---

## 三、 开发者黑科技：无代码构建网页应用（Web App）！

### 【横评比较】Opal 比较 Agent Skills 比较 n8n

- n8n：实现复杂、配置多、功能强大，只适合专业人士！

- Agent Skills：实现简单、普通人能完成、功能强，但需要配置（如第三方调用接口等）

- Opal ：一句话生成！实现超简单！但局限于Google全家桶（无需配置）！功能有限（只网页应用APP）。适合如教学辅助演示附加特色【灵感】


### 3.1 Opal 与 Canvas \[2]

- **Opal (新 Gem)**：用自然语言打造零代码工作流，自动串接 Google 所有的 AI 节点（文字、图片、语音、音乐），最终产出是一个可分享的**互动式网页应用（Web App）**。

![image.png](https://repo.in4tree.com/2026/02/14_1771139159505.png)


**示例1：中英文翻译及发音**

輸入英文文章，翻成中文、提供文章内的英文生字、英文發音、中文解辉、和例句，輸入和輸出：使用繁體中文。

![image.png](https://repo.in4tree.com/2026/02/14_1771139349847.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771139373249.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771139395268.png)


**示例1：冥想**

![image.png](https://repo.in4tree.com/2026/02/14_1771139437704.png)

### 3.2 Gemini + Canvas \[2]

![image.png](https://repo.in4tree.com/2026/02/14_1771139723862.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771139830256.png)

![image.png](https://repo.in4tree.com/2026/02/14_1771139859236.png)


![image.png](https://repo.in4tree.com/2026/02/14_1771139559008.png)


### 3.3 **Google AI Studio**：直接通过对话生成 Web 程序代码。\[2]

 示例：两分钟内生成一个具备重大事件选日的“现代农历网页App”，支持预览、部署及上传至 GitHub。

![image.png](https://repo.in4tree.com/2026/02/14_1771139971866.png)



---

## 四、 视频内容价值评价表

| **视频标题**                                                                                    | **核心摘要**                                | **AI 评分** | 序号  |
| ------------------------------------------------------------------------------------------- | --------------------------------------- | --------- | --- |
| [三个Gemini 3 高级技巧：系统指令 \| 交互禁忌 \| 幻觉规避](https://www.youtube.com/watch?v=jppYKp0dxoA)         | 深度解析底层逻辑，针对幻觉与系统指令提供了极具操作性的模板。          | **98**    | 1   |
| [Gemini 被低估的生產力功能！超越 90% 使用者的「正確打開方式」](https://www.youtube.com/watch?v=JfYYOgMJ33M)         | 覆盖 Opal、Canvas 等最新实验室功能，侧重于多媒体和 App 生成。 | **94**    | 2   |
| [90% 的人都不知道❗️ 被嚴重低估的 Gemini 生產力：超越“對話”的正確打開方式](https://www.youtube.com/watch?v=w1qxSN2qRKc) | 侧重职场实战场景，对三种模式的选择提供了极佳的类比分析。            | **90**    | 3   |


---

## 五、 知识扩充建议 (补充大纲以外的相关内容)

1. **Context Caching (上下文缓存)**：如何存储频繁使用的超长文档以节省 Token 消耗。
    
2. **API 成本分析**：对比 Gemini 1.5 Pro 与 Flash 在大规模自动化任务中的价格优势。
    
3. **多模态原生能力**：如何在不通过文字描述的情况下，直接让 AI 分析视频中的运镜与构图。
    
4. **Google One AI Premium 权益**：详细对比该方案在 Android 系统级集成中的优势。
    
5. **Vertex AI 平台**：针对企业级用户，如何利用 Gemini 进行模型微调 (Fine-tuning)。
    
6. **Imagen 3 指令优化**：Gemini 内部调用绘图模型时的特定参数控制。
    
7. **Chrome 侧边栏集成**：利用浏览器原生集成实现跨标签页的信息提取。
    
8. **AI 安全性 (Safety Settings)**：如何在 AI Studio 中手动调节安全阈值以获取更自由的输出。
    
9. **Function Calling (函数调用)**：让 Gemini 自动触发外部代码工具的配置方法。
    
10. **对比 OpenAI o1 推理模型**：分析 Gemini Thinking 模式与 o1 在解决数学/代码难题上的差异。
    


---

# 【参考】

## ？？？？？专业提示词资料 \[1]\[2]\[3]