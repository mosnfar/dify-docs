# 集成外部 Ops 工具

### 为什么需要 LLMOps 工具

尽管 LLM 拥有出色的推理和文本生成能力，但其内部运作机制仍然难以完全理解，这给基于 LLM 的应用开发带来了挑战。例如：

* 评估输出**质量**
* 推理**成本**评估
* 模型响应**延迟**
* 链式调用、Agent 和工具引入的**调试复杂**性
* 复杂的用户意图理解

而 LangSmith、Langfuse 这类 LLMOps 工具，能够为 LLM 应用提供全面的追踪和深度评估能力，为开发者提供从应用的原型构建到生产、运营的完整生命周期支持。

* **原型阶段**

LLM 应用在原型构建阶段通常涉及提示词测试、模型选择、RAG 检索策略和其他参数组合的快速实验。快速了解模型的执行效果对于此阶段非常重要。接入 Langfuse 可以在跟踪 dify 应用执行的每个步骤，提供清晰的可见性和调试信息，从而让开发者快速定位问题并减少调试时间。

* **测试阶段**

进入测试阶段后，需要继续收集数据以改进和提高性能。 LangSmith 能够将运行作为示例添加到数据集中，从而扩展实际场景的测试覆盖范围。这是将日志系统和评估/测试系统置于同一平台中的一个关键优势。

* **生产阶段**

进入生产环境后，开发团队还需要仔细检查应用关键数据点、增加基准数据集、人工注释以及深入分析运营数据结结果。尤其是在应用大规模使用中，运营和数据团队需要持续观测应用成本和性能，对模型以及应用表现进行优化。

### Dify 与 Ops 工具的集成

使用 Dify Workflow 编排 LLM 应用时，通常涵盖一系列节点和逻辑，具有较高的复杂性。

将 Dify 与外部 Ops 工具集成，有助于打破编排应用时可能面临的 LLM “黑盒”问题。开发者只需要在平台上进行简单的配置，即可追踪应用生命周期中的数据和指标，轻松评估在 Dify 上创建的 LLM 应用质量、性能和成本。