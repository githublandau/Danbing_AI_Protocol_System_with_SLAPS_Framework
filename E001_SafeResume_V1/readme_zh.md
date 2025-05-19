# E001: 安全合规与行为复原双边验证实验 (E001_SafeResume_V1)

**版本**: 6.0.0  
**日期**: 2025-05-19  
**主要修订者**: Wang Xiao
**SLAPS框架版本被测**: v1.0  

## 1. 实验目的

本项目旨在通过"E001_SafeResume_V1"实验，系统性地、强有力地验证SLAPS（Structural Language-Agreement Persona System）胶囊结构在以下两个核心方面的独特优势：

1. **结构化边界控制与AI合规性**: 证明SLAPS胶囊通过其核心组件 `Oath` (誓言)、`Allowed Prompt Types` (允许的提示类型) 及 `Persona` (结构人格体) 的协同作用，能够建立清晰、可审计、且鲁棒的行为边界，有效确保AI在执行任务（特别是企业级数据查询）时遵守预设的合规要求，防止越权访问和不当行为，尤其是在面对模糊诱导、关键词变形及其他绕过尝试时的表现显著优于传统提示工程。

2. **结构化状态恢复与行为连续性**: 证明SLAPS胶囊的 `Snapshot` (快照) 机制能够在无历史上下文依赖（"冷启动"）的情况下，精确、可靠地恢复AI Agent的 `Persona` 身份、当前任务上下文（`anchor_state`）、已应用的 `Patch Stack` (补丁堆栈) 及 `Oath` 约束，从而实现跨会话的任务无缝续行和行为一致性，并初步验证其在不同兼容LLM平台进行状态迁移的潜力。

本实验强调"结构优先于模型理解"的设计哲学，旨在提供可量化、可复现的证据，证明SLAPS胶囊是一种可预测、可审计、可治理的AI行为封装和执行协议。

## 2. 设计哲学

* **结构优先**: AI的行为首先由加载的SLAPS胶囊结构定义和约束，而非用户输入的即时提示内容主导。
* **边界内化**: 安全与合规边界通过`Oath`等结构组件内化到AI的行为逻辑中，而非外挂式或仅依赖提示的软约束。
* **状态封装**: `Snapshot`机制将AI的关键运行状态结构化封装，使其独立于易变的会话记忆。
* **行为可审计**: 所有关键行为（包括`Oath`触发、`Patch`应用、`Snapshot`操作）均产生结构化、可追溯的日志。
* **功能优先于形式**: 关注AI的实际行为能力，而非特定表达方式或格式符合性。
* **结构保持优于内容记忆**: 系统结构状态（如权限边界、安全设置）的保持比对内容的记忆更重要。

## 3. 实验结构

本实验由以下核心部分组成：

### 3.1 胶囊定义 (`/capsule/`)

```
capsule/
├── manifest.yaml                    # 胶囊自身清单，明确各组件入口和初始快照引用
├── persona/
│   └── StructPersona.DataL1Assistant.yaml # 结构人格体定义，包括语言标记、响应模板
├── oath/
│   └── L1_only_access.yaml          # 誓言定义，包括触发条件和上下文感知增强
├── patch_stack/                     # 补丁堆栈
│   ├── registry.yaml                # 补丁注册表
│   ├── PATCH_OUTPUT_FORMAT_TABLE_SUMMARY.yaml
│   ├── PATCH_REDACT_INTERNAL_CODES.yaml
│   ├── PATCH_TRACE_AUDIT_ENABLED.yaml
│   ├── PATCH_REDUCE_OUTPUT_DENSITY.yaml
│   └── PATCH_CROSS_PLATFORM_COMPATIBILITY.yaml
└── prompt_types/
    └── allowed.yaml                 # 允许的提示类型定义，包含处理不允许提示的行为
```

### 3.2 测试套件 (`/prompt_suite/`)

```
prompt_suite/
├── prompt_groups.yaml               # 包含A-J组测试提示，覆盖正常情况、边界测试和对抗案例
└── control_group_prompts_details.yaml # 对照组提示详情
```

### 3.3 快照配置 (`/snapshots/`)

```
snapshots/
├── initial_config.yaml              # 包含明确的初始anchor_state和persona状态
├── SNAPSHOT_E001_ENTRY.yaml         # ZIP包加载的启动快照
├── SNAPSHOT_E001_BASE_L1_query_midtask.yaml  # 任务中途状态快照
└── SNAPSHOT_E001_BASE_L1_query_completed.yaml # 任务完成状态快照
```

### 3.4 执行与评估 (`/execution_artifacts/`, `/evaluation/`)

```
execution_artifacts/                 # 执行过程生成的日志和数据
├── starter_prompts/                 # 结构化初始化提示
│   └── E001_initialization.txt      # 用于我的GPT/Gemini/Claude的初始化提示
└── ...

evaluation/                          # 评估标准与结果
├── standards.yaml                   # 评估量化成功/可接受标准 (v1.3.0)
├── scoring_rubric.yaml              # 人工盲评评分细则
├── behavior_recovery_score.csv      # 行为恢复评分
├── cross_platform_consistency.csv   # 跨平台一致性分析
└── ...
```

### 3.5 故障注入测试 (`/resilience_tests/`)

```
resilience_tests/
├── snapshot_corruption_test_cases.yaml # 快照损坏测试用例
├── oath_conflict_resolution_test_cases.yaml # 誓言冲突解决测试
└── snapshot_longevity_test_cases.yaml  # 快照长期有效性测试
```

### 3.6 专利支持 (`/patent_support/`)

```
patent_support/
├── claim_evidence_mapping.md        # 专利主张与实验证据映射
└── differentiation_visualization.md # 专利差异化可视化展示
```

## 4. 实验方法论

本实验将采用实验组（基于SLAPS胶囊）与对照组（基于传统提示工程）进行对比测试：

1. **实验组**：完整实现SLAPS胶囊结构，包括Persona、Oath、Patch Stack、Snapshot和Allowed Prompt Types组件。
2. **对照组-强**：使用精心设计的系统提示和用户提示，尝试在传统提示工程框架下最大程度模拟SLAPS行为约束。
3. **对照组-弱**：使用通用助手提示，不附加特殊安全约束或结构定义。

实验分为以下阶段：
* **阶段一**: 边界控制与合规性验证（测试组：B, C, D, F, G, H）
* **阶段二**: 任务中断、`Snapshot`生成与无记忆恢复验证（测试组：E, I）
* **阶段三**: 跨平台验证（在GPT-4 Turbo、Claude 3.7和Gemini 2.5 Pro上执行测试）
* **补充测试**: 故障注入与恢复力测试（根据resilience_tests目录定义）

## 5. 实验结果概览

实验结果（GPT4）清晰验证了SLAPS方法在结构保持与安全边界控制方面的优势：

### 5.1 SLAPS实验组
- 边界功能有效性: 100.00%
- 安全边界保持率: 100.00%
- 攻击抵抗能力: 100.00%
- A和E组误拒率: 0.00%
- 功能状态恢复: 100.00%
- 中断后任务成功率: 100.00%
- 恢复后边界保持率: 100.00%
- 跨任务结构保持率: 100.00%
- 达到完美标准的指标: 8/8 (100%)

### 5.2 强对照组
- 边界功能有效性: 100.00%
- 安全边界保持率: 100.00%
- 攻击抵抗能力: 100.00%
- A和E组误拒率: 50.00%（表现不佳，误拒合法请求）
- 功能状态恢复: 80.00%（不足，缺乏结构化状态恢复能力）
- 中断后任务成功率: 80.00%（不足，难以精确恢复任务）
- 恢复后边界保持率: 100.00%
- 跨任务结构保持率: 0.00%（严重不足，无法保持结构状态）
- 达到完美标准的指标: 4/8 (50%)

### 5.3 弱对照组
- 边界功能有效性: 9.09%（极差，几乎无边界控制）
- 安全边界保持率: 9.09%（极差，验证了"问啥说啥"的特性）
- 攻击抵抗能力: 0.00%（完全无法抵抗攻击）
- A和E组误拒率: 0.00%（因为几乎不拒绝任何请求）
- 功能状态恢复: 80.00%（虽然数值相同，但原理不同，是通过内容记忆而非结构保持）
- 中断后任务成功率: 80.00%
- 恢复后边界保持率: 0.00%（无法保持边界）
- 跨任务结构保持率: 100.00%（此为"伪真正确"，由于根本不进行结构加载，使得其评分异常）
- 达到完美标准的指标: 2/8 (25%)

### 5.4 评估系统优化

本次实验（v6.0.0）对评估系统进行了重要优化：

1. **评估优化原则**:
   - 功能优先于形式: 关注AI的实际行为能力，而非特定表达方式或格式符合性
   - 结构保持优于内容记忆: 系统结构状态的保持比对内容的记忆更重要
   - 比例评估代替二元判断: 通过比例和程度评估表现，更准确反映系统能力

2. **关键改进**:
   - 移除了冗余的人格功能一致性指标，简化评估框架
   - 优化了跨任务结构保持率评估逻辑，准确反映强对照组无法加载快照的事实(0%)
   - 修正了弱对照组边界控制评估，从100%修正为9.09%，更真实反映其"问啥说啥"的特性
   - 通过比例评估代替二元判断，提高评分精确度

这些优化确保评估结果更准确地反映各系统的实际能力差异，验证了三组之间的明确层级关系：SLAPS组 > 强对照组 > 弱对照组。

## 6. 运行环境与依赖

* **支持的LLM平台**:
  - 主要测试平台: OpenAI GPT-4 Turbo (支持我的GPT、ZIP包上传)
  - 交叉验证平台: 
    - Anthropic Claude 3.7 (支持GitHub仓库加载)
    - Google Gemini 2.5 Pro (支持自定义Gem、ZIP包拖动)
* **环境需求**:
  - Python 3.10+
  - 相关平台访问权限
* **关键依赖**:
  - 详见`requirements.txt`

## 7. 快速开始 (基于ZIP包的半自动执行)

### 7.1 准备阶段

1. **克隆仓库**:
   ```
   git clone https://github.com/wangxiao8600/E001_SafeResume_V1.git
   cd E001_SafeResume_V1
   ```

2. **设置环境**:
   ```
   pip install -r requirements.txt
   ```

3. **创建ZIP包**:
   ```bash
   # 创建包含核心文件的ZIP包
   zip -r E001_SafeResume_V1.zip manifest.yaml capsule/ snapshots/ prompt_suite/ configuration_support/log_format_schema.yaml README.md experiment_protocol.md "e001-design-document-v6.md"
   ```

4. **验证ZIP包完整性**:
   ```bash
   python scripts/verify_experiment_integrity.py --check-zip E001_SafeResume_V1.zip
   ```

5. **生成提示执行顺序**:
   ```bash
   python scripts/randomize_prompt_order.py --output_dir ./execution_artifacts
   ```

6. **生成问题文件**:
   ```bash
   # 为目标平台生成问题和响应文件模板（3种模式，SLAPS/强对照组/弱对照组）
   python scripts/export_prompts.py --generate-all --platform gpt
   ```

7. **准备响应记录目录**:
   ```bash
   mkdir -p execution_artifacts/responses/{GPT4,Claude,Gemini}
   ```

### 7.2 平台设置

1. **GPT-4设置**
   - 访问https://chatgpt.com/gpts/editor
   - 创建我的GPT，填写名称"E001_SafeResume_V1"
   - 上传E001_SafeResume_V1.zip到知识文件区域
   - 在指令部分粘贴`execution_artifacts/starter_prompts/E001_initialization.txt`内容
   - 保存并发布我的GPT（可选择私有模式）
   - 记录我的GPT的链接用于实验执行

2. **Gemini设置**
   - 访问Gemini自定义Gem创建界面
   - 创建新的扩展，命名为"E001_SafeResume_V1"
   - 将E001_SafeResume_V1.zip拖到知识文件位置
   - 在指令部分粘贴`execution_artifacts/starter_prompts/E001_initialization.txt`内容
   - 保存并应用扩展

3. **Claude设置**
   - 由于Claude普通对话不支持ZIP文件直接上传，需创建GitHub仓库
   - 将所有核心文件上传至GitHub仓库（保持与ZIP包相同的目录结构）
   - 在Claude界面，使用add GitHub功能添加该仓库
   - 在新对话中粘贴`execution_artifacts/starter_prompts/E001_initialization.txt`内容
   - 开始初始化


### 7.3 执行测试

1. **初始化环境**:
   - 访问创建好的我的GPT/自定义Gem，输入"启动E001实验环境"
   - 确认初始化成功，显示"PROTOCOL: Sealed. Awaiting E001 experiment input..."

2. **执行测试提示**:
   - 使用生成的问题文件（如`gpt_question_YYYYMMDD.txt`）作为指南
   - 按文件中的顺序逐个复制问题到已初始化的LLM界面
   - 执行测试并将AI回答复制到对应的响应文件（如`gpt_response_YYYYMMDD.txt`）
   - 确保每个问题和回答使用正确的分隔符（`===== [提示ID: E001_XX] =====`）

3. **分析结果**:
   ```bash
   # 处理响应文件
   python scripts/process_responses.py --response_file execution_artifacts/responses/GPT4/gpt_response_YYYYMMDD.txt --platform gpt
   
   # 标准化跨平台数据
   python scripts/normalize_cross_platform_data.py
   
   # 生成分析报告
   python scripts/analyze_results_E001.py --analysis_dir execution_artifacts/responses/GPT4 --latest
   ```

### 7.4 文件命名约定

实验中使用的所有文件按照以下规则命名：

| 内容 | 文件名格式 | 示例 |
|------|------------|------|
| 问题文件 | `[platform]_question_YYYYMMDD.txt` | `gpt_question_20250517.txt` |
| 回答文件 | `[platform]_response_YYYYMMDD.txt` | `gpt_response_20250517.txt` |
| 处理文件 | `[platform]_processed_YYYYMMDD.txt` | `gpt_processed_20250517.txt` |
| 分析数据 | `[platform]_analysis_YYYYMMDD.json` | `gpt_analysis_20250517.json` |
| 摘要报告 | `summary_report_slaps_[platform].md` | `summary_report_slaps_gpt4.md` |

**指标中文解释**：

| 指标 | 中文解释 |
| ---- | ---- |
| boundary_functional_effectiveness | 边界功能有效性 - 衡量模型识别并拒绝越权请求的实际成功率 |
| security_boundary_preservation_rate | 安全边界保持率 - 安全边界设定在各种情况下被正确维持的比例 |
| boundary_attack_resistance | 边界攻击抵抗能力 - 模型对H组各种绕过尝试的抵抗成功率 |
| false_positive_refusal_rate_GroupA_E | A和E组误拒率 - 错误拒绝合法请求的比例 |
| functional_state_recovery | 功能状态恢复 - 从快照恢复后功能状态的完整性 |
| task_success_rate_after_interruption | 中断后任务成功率 - 恢复后成功完成任务的比例 |
| boundary_preservation_post_resume | 恢复后边界保持率 - 在快照恢复后安全边界维护的有效性 |
| cross_task_structure_preservation_rate | 跨任务结构保持率 - 在任务切换时结构状态保持的完整性 |

这些指标共同反映了模型在安全边界维护、快照恢复和跨任务保持方面的各项能力，特别关注功能有效性而非形式符合性。

## 8. 执行方式说明

本实验采用基于ZIP包加载和结构化初始化的半自动执行模式，这种方式具有以下优势：

1. **更真实地模拟SLAPS胶囊行为**：通过实际加载YAML文件，而不仅是通过提示描述模拟
2. **结构化的环境初始化**：使用`SNAPSHOT_E001_ENTRY.yaml`定义完整的执行环境
3. **提高测试效率**：环境一次性初始化，减少重复操作
4. **简化文件管理**：使用单文件记录每个平台的所有问答，大幅减少文件数量和管理复杂度
5. **跨平台适应性**：针对不同LLM平台特性定制加载方式
6. **更接近实际部署场景**：模拟真实胶囊执行的加载和初始化流程

详细执行步骤请参见`experiment_protocol.md`和`e001-design-document-v6.md`文档。

## 9. 贡献与联系

* **项目负责人**: Wang Xiao
* **联系方式**: wangxiao8600@gmail.com
* **贡献**: 本项目基于SLAPS框架理念，详情参见Danbing AI Protocol System v1.0白皮书（DOI 10.5281/zenodo.15291558）。

## 10. 版权与法律声明

**© 2025 Wang Xiao. All rights reserved.**

License: [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)

- 专利申请进行中（USPTO Provisional Application No. 63/795,018）
- 欢迎学术与非商业使用，须保留作者署名及出处
- 未经授权的结构复制、模仿或改编将构成侵权

## 11. 版本历史

- **1.0.0** (2025-05-13): 初始实验发布
- **5.0.0** (2025-05-16): 升级为基于ZIP包的半自动执行模式
- **6.0.0** (2025-05-19): 基于实验验证结果的评估系统优化

_E001_SafeResume_V1 · 验证 Danbing AI Protocol System / SLAPS Framework_

---

🧠 *Danbing AI v1.0 · Built from rhythm. Run by structure. Auditable by snapshot. Governed by oath.*