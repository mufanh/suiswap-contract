# 《Suiswap 智能合约审计报告》

<u>Suiswap 智能合</u>约审计报告



1 执行摘要



### 1.1 项目信息&#xA;



| 描述&#xA;   | Suiswap 是由 Vivid Network 在 SUI 区块链上构建的去中心化代币交易平台和交易所，旨在为 SUI 生态系统提供安全、快速、灵活的交易环境。&#xA;                                                                                   |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 类型&#xA;   | DEX&#xA;                                                                                                                                                                 |
| 审计机构&#xA; | MoveBit&#xA;                                                                                                                                                             |
| 时间线&#xA;  | 2023 年 5 月 24 日 - 2023 年 6 月 6 日&#xA;                                                                                                                                    |
| 编程语言&#xA; | Move&#xA;                                                                                                                                                                |
| 平台&#xA;   | Sui&#xA;                                                                                                                                                                 |
| 方法&#xA;   | 架构审查、单元测试、手动审查&#xA;                                                                                                                                                      |
| 源代码&#xA;  | [https://github.com/vividnetwork/suiswap-audit](https://github.com/vividnetwork/suiswap-audit)                                                                           |
| 提交记录&#xA; | a46d60ac35f6a3a08e01be579b3cc6df840de62e 3d1dc12482231b34726668a179123edd2bceb990 3c8da82745fdda1e05cbf127e3368f8b319b3fc2 66795c96f17d87a15c8e6f9f9e546932c1a18d4f&#xA; |

### 1.2 审计范围内的文件&#xA;

以下是最后审查文件的 SHA1 哈希值：




| ID&#xA;  | 文件&#xA;                      | SHA-1 哈希值&#xA;                                |
| -------- | ---------------------------- | --------------------------------------------- |
| PMS&#xA; | sources/permission.move&#xA; | 531ccb4a588c2138c68b4266e73d705e69d263fa&#xA; |
| POL&#xA; | sources/pool.move&#xA;       | 52d6bbe121bac744b78dc6a887053d355b84ed2c&#xA; |
| RTO&#xA; | sources/ratio.move&#xA;      | dcf2a43ae58ba9eff5fd7ce5cbbb25094f5eaee9&#xA; |
| SBC&#xA; | sources/sbalance.move&#xA;   | 10f64b4a8762c1c8d1753c0f657b2c486566ef3d&#xA; |
| TKN&#xA; | sources/token.move&#xA;      | aaacbbfee72cc2d12e94af0d3d196a0b12aee3a2&#xA; |
| UTL&#xA; | sources/utils.move&#xA;      | 6d177eac94f38f6d8ee1310f860117ec534f68f4&#xA; |
| VPT&#xA; | sources/vpt.move&#xA;        | fdfdc8cbe9a7b70e83a132a755e7aea130ce16d7&#xA; |

### 1.3 问题统计&#xA;



| 项目&#xA;       | 数量&#xA; | 已修复&#xA; | 部分修复&#xA; | 已确认&#xA; |
| ------------- | ------- | -------- | --------- | -------- |
| 总计&#xA;       | 20&#xA; | 17&#xA;  | 1&#xA;    | 2&#xA;   |
| 信息性问题&#xA;    | 2&#xA;  | 2&#xA;   |           |          |
| Minor&#xA;    | 9&#xA;  | 7&#xA;   |           | 2&#xA;   |
| Medium&#xA;   | 4&#xA;  | 3&#xA;   | 1&#xA;    |          |
| Major&#xA;    | 5&#xA;  | 5&#xA;   |           |          |
| Critical&#xA; |         |          |           |          |

### 1.4 MoveBit 审计分类&#xA;

MoveBit 旨在评估代码库的安全相关问题、代码质量以及是否符合规范和最佳实践。我们团队关注的可能问题包括（但不限于）：




*   交易顺序依赖


*   时间戳依赖


*   位操作导致的整数溢出 / 下溢


*   舍入错误数量


*   拒绝服务 / 逻辑疏忽


*   访问控制


*   权力集中化


*   业务逻辑与规范冲突


*   代码克隆、功能重复


*   Gas 消耗


*   任意代币铸造


*   未检查的 CALL 返回值


*   能力权限流


*   见证类型


### 1.5 方法论&#xA;

安全团队采用 “测试与自动化分析”、“代码审查” 和 “形式验证” 策略，以最接近真实攻击的方式对代码进行全面安全测试。安全测试的主要入口和范围在《审计目标》的约定中说明，可根据实际测试需要扩展到范围以外的场景。本次安全审计的主要类型包括：




1.  **测试与自动化分析**

*   检查项：状态一致性 / 失败回滚 / 单元测试 / 值溢出 / 参数验证 / 未处理错误 / 边界检查 / 编码规范。


1.  **代码审查**

*   代码范围见 1.2 节。


1.  **形式验证**

*   使用 Move Prover 对关键函数进行形式验证。


1.  **审计流程**

*   在测试网或主网上进行相关安全测试；


*   审计过程中如有疑问，及时与代码所有者沟通，代码所有者应积极配合（可能包括提供最新稳定源代码、相关部署脚本或方法、交易签名脚本、交易所对接方案等）；


*   审计过程中的必要信息将及时为审计团队和代码所有者做好记录。


2 总结



本报告由 Vivid Network 委托，旨在识别 Suiswap 智能合约源代码中任何潜在问题和漏洞，以及不属于官方认可库的任何合约依赖项。在本次审计中，我们利用了各种技术，包括手动代码审查和静态分析，以识别潜在的漏洞和安全问题。


审计期间，我们发现了 20 个不同严重程度的问题，如下所列：




| ID&#xA;     | 标题&#xA;                                                               | 严重程度&#xA;   | 状态&#xA;   |
| ----------- | --------------------------------------------------------------------- | ----------- | --------- |
| VPT-01&#xA; | 未使用的常量&#xA;                                                           | Minor&#xA;  | 已修复&#xA;  |
| VPT-02&#xA; | 布尔值的不必要比较&#xA;                                                        | Minor&#xA;  | 已修复&#xA;  |
| TKN-01&#xA; | do\_withdraw\_token\_bank\_admin\_balance 函数缺少事件日志&#xA;               | Minor&#xA;  | 已修复&#xA;  |
| TKN-02&#xA; | do\_add\_token\_ido\_whitelist 函数缺少权限验证&#xA;                          | Major&#xA;  | 已修复&#xA;  |
| TKN-03&#xA; | do\_claim\_token\_airdrop\_token\_legacy 函数中潜在的事件绕过&#xA;              | Minor&#xA;  | 已修复&#xA;  |
| TKN-04&#xA; | do\_increase\_token\_supply 函数的中心化风险&#xA;                             | Medium&#xA; | 部分修复&#xA; |
| TKN-05&#xA; | token.move 的生产代码和测试代码未分离&#xA;                                         | Major&#xA;  | 已修复&#xA;  |
| TKN-06&#xA; | 为 share\_minted 添加断言验证&#xA;                                           | Minor&#xA;  | 已修复&#xA;  |
| TKN-07&#xA; | do\_swap\_x\_to\_y\_direct 和 do\_swap\_x\_to\_y\_direct 函数中的断言错误&#xA; | Medium&#xA; | 已修复&#xA;  |
| TKN-08&#xA; | do\_claim\_token\_airdrop\_token\_legacy 函数中的重复代码&#xA;                | 信息性&#xA;    | 已修复&#xA;  |
| TKN-09&#xA; | do\_send\_staked\_token 函数中记录事件的 token\_type 值不正确&#xA;                | Minor&#xA;  | 已修复&#xA;  |
| TKN-10&#xA; | do\_create\_registry 和 do\_create\_token\_farm 函数缺少验证&#xA;            | Minor&#xA;  | 已修复&#xA;  |
| POL-01&#xA; | 缺少事件发射&#xA;                                                           | Minor&#xA;  | 已确认&#xA;  |
| POL-02&#xA; | add\_liquidity\_direct\_impl 函数缺少总流动性限制和最小锁定&#xA;                     | Major&#xA;  | 已修复&#xA;  |
| POL-03&#xA; | do\_create\_registry 函数中 admin\_fee 的初始化值与注释不一致&#xA;                  | 信息性&#xA;    | 已修复&#xA;  |
| POL-04&#xA; | 由于在计算 th\_fee 前从 balance 中扣除 admin\_fee 导致 th\_fee 计算错误&#xA;          | Minor&#xA;  | 已确认&#xA;  |
| POL-05&#xA; | ss\_compute\_y 函数中错误的循环终止和不一致的实现&#xA;                                 | Medium&#xA; | 已修复&#xA;  |
| POL-06&#xA; | compute\_deposit 函数中 XY 代币到 LP 的转换不完整&#xA;                            | Major&#xA;  | 已修复&#xA;  |
| POL-07&#xA; | 管理员权限允许操纵流动性和规避交易费用&#xA;                                              | Major&#xA;  | 已修复&#xA;  |
| POL-08&#xA; | ss\_compute\_mint\_amount\_for\_deposit 函数缺少验证&#xA;                   | Medium&#xA; | 已修复&#xA;  |

3 参与方流程



以下是 Suiswap 智能合约中各相关角色及其权限：**管理员**



*   管理员可以通过 increase\_token\_supply 函数铸造 TOKEN 代币，铸造上限为 100000000000000000000。


*   管理员有权铸造和销毁代币，允许随意发行或销毁代币。


*   管理员可以通过 do\_change\_basis 函数修改 pool.balance.bx 和 pool.balance.by 的值来操纵池的汇率，这将影响交换过程中收到的实际代币数量。


*   管理员可以通过 create\_pool 函数创建池。


*   管理员可以通过 change\_fee 函数修改 admin\_fee、lp\_fee 和 th\_fee。


*   管理员可以冻结 / 解冻任何池，无论该池是由管理员还是用户创建的。


4 审计发现



### VPT-01 未使用的常量&#xA;



*   **严重程度**：Minor


*   **状态**：已修复


*   **代码位置**：sources/vpt.move #L8, L12, L13; sources/sbalance.move#L13; sources/pool.move #L27, L29, L30, L52, L54, L64, L70, L76, L78, L96, L110, L112, L114


*   **描述**：合约中声明的某些变量未在合约的任何函数或逻辑中引用或使用。这些未使用的变量增加了代码库的不必要复杂性，并可能使试图理解合约功能的开发人员或审计人员感到困惑。


*   **建议**：除非计划在未来的更新或添加中使用这些变量，否则建议将其删除，以提高代码的可读性和可维护性。


*   **解决方案**：客户已按照我们的建议修复了该问题。


### VPT-02 布尔值的不必要比较&#xA;



*   **严重程度**：Minor


*   **状态**：已修复


*   **代码位置**：sources/vpt.move #L25; sources/pool.move #L681, L1033


*   **描述**：合约中存在使用条件语句将布尔值与 false 或 true 进行比较的情况。这种方法在代码中引入了不必要的复杂性和冗余，因为布尔值可以直接在 if 语句或循环中用作条件。


*   **建议**：建议在使用布尔值时遵循最佳实践，避免与 false 或 true 进行不必要的比较。


*   **解决方案**：客户已按照我们的建议修复了该问题。


### TKN-01 do\_withdraw\_token\_bank\_admin\_balance 函数缺少事件日志&#xA;



*   **严重程度**：Minor


*   **状态**：已修复


*   **代码位置**：sources/token.move #L736


*   **描述**：do\_withdraw\_token\_bank\_admin\_balance 函数在提取管理员余额时未记录事件。


*   **建议**：为 do\_withdraw\_token\_bank\_admin\_balance 函数添加事件日志。


*   **解决方案**：客户已按照我们的建议修复了该问题。


### TKN-02 do\_add\_token\_ido\_whitelist 函数缺少权限验证&#xA;



*   **严重程度**：Major


*   **状态**：已修复


*   **代码位置**：sources/token.move #L936


*   **描述**：do\_add\_token\_ido\_whitelist 函数缺少权限验证，允许任何人将自己的地址添加到代币 IDO 白名单中。


*   **建议**：指定特定地址或角色作为管理员，有权修改代币 IDO 白名单。只有授权管理员才能调用 do\_add\_token\_ido\_whitelist 函数。


*   **解决方案**：客户已按照我们的建议修复了该问题。


附录 1 问题等级





*   **信息性问题**：通常是改进代码风格或优化代码的建议，不影响整体功能。


*   **Minor 问题**：与最佳实践和可读性相关的一般建议，不构成直接风险，鼓励开发人员修复。


*   **Medium 问题**：不可利用的问题，不属于安全漏洞，除非有特殊原因，否则应修复。


*   **Major 问题**：安全漏洞，使用户的部分敏感信息面临风险，通常不可直接利用，所有 Major 问题都应修复。


*   **Critical 问题**：可直接利用的安全漏洞，使用户的敏感信息面临风险，所有 Critical 问题都应修复。


附录 2 免责声明



本报告基于提供的材料和文件范围，在提供时进行了有限审查。结果可能不完整，且不包括所有漏洞。审查和本报告按 “原样”、“现有” 和 “可用” 的基础提供。您同意，您的访问和 / 或使用（包括但不限于任何相关服务、产品、协议、平台、内容和材料）将由您自行承担风险。本报告不暗示对任何特定项目或团队的认可，也不保证其安全性。这些报告不应以任何方式被任何第三方依赖，包括用于做出购买或出售产品、服务或任何其他资产的决定。在法律允许的最大范围内，我们对本报告及其内容、相关服务和产品以及您的使用，免除所有明示或暗示的保证，包括但不限于适销性、特定用途适用性和不侵权的暗示保证。
