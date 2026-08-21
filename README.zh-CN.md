# dsh-decision-effect-proof

离线、确定性地对账 DSH 的授权决策收据与 effect 收据。它检查拒绝后仍产生 effect、允许后未结算、请求/状态/策略摘要错配、确认缺失、幂等摘要重放、重复与乱序，并生成内容寻址、写后回读验证的 JSON 报告。

它不是审批器、策略引擎、动作执行器、签名格式或提示词包装。现有审批/权限插件负责决定与拦截，ACTA/SEP 等体系负责签名授权链；本插件只补“**获准不等于已执行**”这一窄边界。报告明确声明：它只能证明所提供收据的一致性，不能凭收据证明现实 effect 确已发生。

安装：`dsh plugin --profile web add github:dongsheng123132/dsh-decision-effect-proof#COMMIT`。DSH 工具为 `dsh_decision_effect_inspect`、`dsh_decision_effect_verify`；独立 MCP 工具为 `decision_effect_inspect_inline`、`decision_effect_verify_inline`。输入只允许摘要和有界标识，不接收原始参数、输出、正文、提示词、消息或秘密。
