---
标题:     openEuler 社区 AI 辅助代码提交规范
类别:     信息整理
摘要:     规范在 openEuler 社区内使用 AI 辅助生成或修改代码的披露、合规与质量要求
作者:     Jianmin Wang (hi at jimmie.me)
状态:     初始化
编号:     oEEP-0025
创建日期: 2026-02-02
修订日期: 2026-02-04
---

## 背景/目标/原则

AI 编程工具在社区内快速普及，显著提升效率，但也带来代码来源不清、许可不明、误用保密信息、潜在安全缺陷、审查成本上升等风险。为了保持社区信任、可持续协作与合规性，需要统一最低披露与责任要求，并给评审者提供可操作的审查依据。

目标：

- 明确 AI 辅助代码提交的范围、职责和最低合规要求。
- 建立可审查、可追溯的披露与自检机制。
- 保护社区成员与贡献者的合规权益，降低安全与版权风险。

原则：

- 透明披露：AI 参与程度可被审查者理解
- 责任归属：责任主体均为自然人，不转移给工具
- 合规优先：遵循许可证、隐私与安全要求
- 最小必要：披露与记录以便评审为限，不强制暴露敏感信息
- 辅助使用：AI 可辅助提交、辅助评审，但不能替代人类判断

## 术语

- AI 辅助代码：由 AI 工具生成或在 AI 建议基础上修改的代码、配置、文档或测试用例。
- 关键变更：影响行为逻辑、安全边界、许可声明、接口兼容性、性能或可维护性的改动。
- 披露：在提交信息（PR 描述或 Commit Message）中说明 AI 参与情况及必要上下文。

## 范围/相关人员及职责

### 适用范围

- 适用于 openEuler 社区内的代码、构建脚本、spec、配置、测试、文档等提交。
- 同样适用于外部补丁搬运或第三方代码引入（包含 AI 参与时）。

### 责任主体

- 提交者：对代码正确性、合规性与安全性负责，确保满足社区规范。
- 评审者：基于披露信息进行必要的审查与追溯，可使用 AI 工具辅助分析，但 AI 不得作为唯一或最终裁决依据。

## 规范与要求

### 1. 披露要求

- 存在关键变更的 AI 辅助代码需要在提交信息中进行披露。如果存在影响行为逻辑、安全边界、许可声明、接口兼容性、性能或可维护性的改动，则视为关键变更。
- 当是否构成关键变更存在合理争议时，建议优先披露。
- 如果需要披露，在提交信息中需要包含 `Assisted-by: <tool>` 或 `Generated-by: <tool>`
- 为便于评审并提升透明度，建议在提交信息中披露以下内容：
  - 说明 AI 参与的范围与程度（例如：生成主体代码、改写功能实现、优化测试、翻译文档）。
  - 在已知或可获取的情况下，提供工具和模型名称与版本。
  - 说明是否做人工验证
- 社区不要求提交完整的提示词、聊天记录或模型交互原文，除非提交者自愿且不涉及敏感信息。
- 以下情形可不披露：拼写与语法修正、机械性格式调整、简单自动补全且不改变逻辑。

参考建议披露信息模板：

- AI 使用情况：是/否
- 使用范围：生成/改写/优化/翻译
- 工具、模型与版本：
- 人工验证：已做/计划做（简要说明）

### 2. 合规与许可

- 提交者必须在其合理认知范围内确认，所提交的 AI 生成内容不包含其已知会侵犯第三方版权的内容。
- 提交者必须确认其对所提交的 AI 生成内容拥有合法权利，可将该内容贡献至本项目，并按照本项目许可证进行再许可和分发。
- 提交者必须确认其所使用的 AI 工具的使用条款不限制其将生成内容按照本项目许可证进行贡献、再许可和分发。
- 若提交者已知或合理应当知晓其包含可识别来源的代码片段与已知开源项目在结构、命名、注释或实现逻辑上实质相似，需明确来源并遵循其许可证。
- 项目维护者保留要求提供来源说明、修改或拒绝包含 AI 生成内容的提交的权利。

### 3. 安全与质量

- 关键变更需提供最小可行的测试或验证说明。
- 提交者必须理解并能解释所提交的逻辑；以“AI 这么生成的”为由无法解释的提交可被拒绝。
- 评审者可要求补充测试证据、拆分提交或替换实现。

### 4. 责任与可追溯

- 任何 AI 生成内容均视为提交者的贡献，由提交者承担责任。
- 评审者有权对披露不足、风险不明或质量欠佳的提交拒绝或要求修改。
- 对明显不理解代码、无法解释变更、或反复提交低质量内容的贡献者，可按社区规则处理。

## 提交与评审流程（建议）

1. 提交前自检
   - 确认 AI 工具使用范围、来源与许可
   - 运行必要测试或静态检查
2. 提交时披露
   - 如果需要披露，在提交信息中需要包含 `Assisted-by: <tool>` 或 `Generated-by: <tool>`
   - 根据实际情况参考建议披露信息模板说明 AI 使用情况
3. 评审阶段
   - 评审者基于披露信息进行重点审查
   - 必要时要求补充测试、拆分或替换实现
   - 评审者参考检查点（非强制）
      - 披露信息是否完整、清晰
      - 提交者是否能解释关键逻辑
      - 是否存在明显的许可或安全风险
      - 测试与验证是否覆盖关键路径
4. 合入后跟踪
   - 发现问题时按常规流程处理并复盘 AI 使用风险

## 示例

示例 1（需要披露）：

- 使用 AI 生成了新的调度算法实现，涉及核心逻辑调整
- 已人工验证并补充单元测试

示例 2（可不披露）：

- 使用 AI 辅助修正文档拼写错误与中英文表述

示例 3（建议披露）：

- 使用 AI 对现有函数进行性能优化，未改变接口但调整了实现逻辑

## 参考链接

- [Fedora Council Policy: AI-Assisted Contributions](https://docs.fedoraproject.org/en-US/council/policy/ai-contribution-policy/)
- [Apache Software Foundation: Generative Tooling Guidance](https://www.apache.org/legal/generative-tooling.html)
- [Linux Foundation: Generative AI Policy](https://www.linuxfoundation.org/legal/generative-ai)
- [Drupal: Proposed guidelines for AI contribution](https://www.drupal.org/project/governance/issues/3565917)
- [DigitalOcean: Contributing AI-Generated Code with Care](https://www.digitalocean.com/community/tutorials/ai-coding-tools-open-source)
- [GNOME Shell Extensions Review Guidelines](https://gjs.guide/extensions/review-guidelines/review-guidelines.html)
- [Code provenance - QEMU documentation](https://www.qemu.org/docs/master/devel/code-provenance.html)
- [NetBSD Commit Guidelines](https://www.netbsd.org/developers/commit-guidelines.html)
