# **大综合1**
| 版本 | 链接 |
| ---- | ---- |
| English 关键词版本 | [跳转到页面](English.md) |
|Normal English | [跳转到页面](for_recitation.md) |


```  
  8 写 7 修电脑可以放弃
  每一点列出来
  c 内置函数：printf scanf 

```

## **计算机系统原理(Computer System Fundamentals)**
- EEPROM (Electrically Erasable Programmable read only memory) 
  - 用途和特性
    - EEPROM 是一种**带电可擦可编程只读存储器**，掉电后数据不丢失。可以擦除已有信息并重新编程，广泛用于即插即用设备，如 U 盘。

    - 用途
      - 数据存储：保存用户设定、设备参数等小型非易失性数据。
      - 配置存储：嵌入式系统中存储固件或硬件配置信息。
      - 固件更新：部分设备用于存储可更新的代码或校准数据。
    - 特性
      - 非易失性：断电后数据不会丢失。
      - 可擦写：电气方式多次擦写，但有擦写寿命（通常 10,000～1,000,000 次）。
      - 字节级操作：支持逐字节读写，灵活性高。
      - 慢速写入：写入速度比读取慢。
- RAM
  - 静态RAM (SRAM) 和动态RAM (DRAM) 比较
    - DRAM 则适合主存，强调容量和成；SRAM 适合高速缓存，强调速度；

        | **Characteristic** | **DRAM** | **SRAM** |
        |--------------------|----------|----------------|
        | **Storage** | **Capacitance**(电容) & **Transistor**（晶体管） | **Transistor**（晶体管） |
        | **Refresh**    | **refresh regularly** （定期刷新）| **Not refresh** |
        | **Speed**        | Slow    | Fast   |
        | **Power**        | High  | Low |
        | **Density**（密度）| High |Low |
        | **Cost**        | Low    | High  |
        | **Apply**        | Memory | CPU,GPU |

    - 主存和缓存的功能与使用
      - 主存（RAM）
        - **功能**：存储当前运行的程序和数据，支持多任务处理。
        - **使用**：操作系统和应用程序在主存中加载并执行指令，存储正在使用的数据。
      - 缓存（Cache）
        - **功能**：加速CPU对主存中数据的访问。存储热点数据，减少访问延迟。
        - **使用**：CPU通过缓存提高对数据的访问速度，减少从主存读取的次数。
      - 主存 vs 缓存 (比较)
        | 特性 | 主存（RAM） | 缓存（Cache） |
        | ---- | --------- | ------------ |
        | 速度 | 较慢 | 非常快 |
        | 目的 | 存储程序和数据 | 加速CPU访问数据 |
        | 访问方式 | 由CPU或其他硬件直接访问 | CPU自动管理缓存内容，通常透明给应用程序 |
        | 成本 | 较低 | 较高 |

- 虚拟内存 (Virtual Memory)
  - 虚拟内存是操作系统用来扩展物理内存的一种技术，通常通过硬盘的交换空间来实现。

- 总线系统
  - 地址总线
    - 地址总线的主要作用是传输地址信息。处理器通过地址总线向内存或外设发送目标地址，以指示数据操作的位置。(单向)
    -  **单向传输**
      - 地址总线通常是单向传输，即地址信息从处理器传向外部设备（如内存、I/O 设备），而不是相反。
    -  32 位 -> 寻址 4 GB 内存 (位宽越大，地址空间越大，计算机能支持的内存或设备数量越多)
   
  - 数据总线（Data Bus）:传输数据内容，与地址总线一起工作。
    - Data Bus是计算机总线系统中的一种总线，用于在处理器、内存以及其他设备之间传输数据。它是总线系统的核心部分，与地址总线和控制总线协同工作，完成信息的传递与处理。
    - **双向传输**
    - 位宽越大，数据总线每秒传输的数据量越多，系统性能越高
    - 并行性: 数据总线是并行传输的，数据位会通过不同的总线线路同时传输。
     
  - 控制总线 (Control Bus) :传输控制信号，协调设备之间的通信。
    - 是计算机总线系统的一部分，用于在处理器、内存和外部设备之间传递控制信号。这些信号指示操作的类型（如读或写）以及数据传输的方向，并协调各个部件的工作。
    - **大部分情况都是双向**
    - 传递控制信号，协调计算机系统各部件的工作。

    - **NMI（不可屏蔽中断）**
      - **作用**：用于处理紧急事件或硬件故障，无法被屏蔽，确保紧急情况得到优先响应。
      - 触发方式: NMI 主要是由硬件触发的
        - 硬件故障：例如，CPU 检测到某些硬件故障（如内存错误、芯片过热等），会生成 NMI。

      - 处理步骤：当 NMI 发生时，操作系统内核会接管并中断当前的任务。
        - 保存上下文：首先，系统会保存当前任务的上下文（如寄存器状态），以便处理完 NMI 后能够恢复。
        - 处理中断：操作系统会运行一个专门处理 NMI 的中断服务程序。这个服务程序会根据 NMI 的原因执行适当的动作。
        - 恢复操作：一旦 NMI 处理完毕，系统会恢复到原来的状态，继续执行之前被中断的任务。

- 真值表 !!!
  - **用于描述逻辑电路的输入与输出关系。**

      | A | B | C | A and B | A or C | not B | (A and B) or (not B) |
      |---|---|---|---------|--------|-------|----------------------|
      | 0 | 0 | 0 |    0    |   0    |   1   |          1           |
      | 0 | 0 | 1 |    0    |   1    |   1   |          1           |
      | 0 | 1 | 0 |    0    |   0    |   0   |          0           |
      | 0 | 1 | 1 |    0    |   1    |   0   |          0           |
      | 1 | 0 | 0 |    0    |   1    |   1   |          1           |

## 系统软件与工具
- **实用程序软件**
  - **作用**：
    - 增强操作系统的功能，例如资源管理器、磁盘碎片整理等。
      - 磁盘清理：帮助清理硬盘上的临时文件、缓存和不必要的文件，以释放存储空间并提高系统性能。
      - 磁盘碎片整理：对硬盘上的文件进行重新排序，减少数据访问的延迟，从而提高计算机的读取速度。
  - 例子：
    - 系统清理工具（如CCleaner）
    - 压缩解压工具（如WinRAR、7-Zip）
    - 备份与恢复工具（如Acronis True Image）
    - 磁盘管理工具（如Partition Wizard）
    - 防病毒与安全工具（如Malwarebytes）
    - 文件管理工具（如Total Commander）
    - 网络工具（如Wireshark）
    - 驱动更新工具（如Driver Booster）
 
- **备份与恢复**
  - **完整备份的作用和文件属性变化**：
    
    - 增量备份、完全备份、差异备份
      - 完全备份（Full Backup）：是指对所有选定的文件和数据进行完整备份，通常是一个初始备份。每次执行完整备份时，备份的数据都是完整的，不依赖任何之前的备份。
        - 优点：恢复过程简单、快捷，因为数据是完整的。
        - 缺点：占用存储空间较多，并且备份时间较长。
      
      - 增量备份（Incremental Backup）：只备份自上次备份以来发生变化的文件。增量备份通常依赖于上一次备份的结果，只有更改过的文件会被备份。
        - 优点：备份速度快，占用空间小。
        - 缺点：恢复过程较复杂，因为恢复时需要使用最后的完全备份和所有增量备份。
      
      - 差异备份（Differential Backup）：备份自上一次完全备份以来发生变化的所有文件。每次差异备份都会备份自上次完全备份以来的所有更改文件。
        - 优点：比增量备份的恢复过程简单，但比完全备份的恢复过程慢。
        - 缺点：随着备份次数的增加，差异备份占用的空间会逐渐增大。
      
      - Archive Flag:
        
        - 归档标志是文件系统中的一种属性，它通常用于指示文件自上次备份以来是否已发生更改。操作系统通过该标志帮助备份工具识别哪些文件是新的或被修改的，以便进行增量或差异备份。
        
        - 步骤:
          - 设置归档标志：当文件内容被修改时，操作系统会自动设置归档标志（在文件系统中将此属性设置为“启用”），表示该文件自上次备份以来已更改。
          
          - 备份时的作用：备份程序在执行增量备份或差异备份时，会检查文件的归档标志。如果标志为“启用”，则表示该文件自上次备份以来已被修改，备份程序将其包括在备份中。
  
          - 归档标志重置：当备份程序执行完备份后，会将归档标志重置为“禁用”，表示该文件已经被备份过了。对于增量备份和差异备份，重置归档标志是非常重要的步骤。

## 软件开发导论
- 基本编程概念
  - 变量类型
    - 整数 Integer、字符 Character、字符串 String、实数 Real（小数包含在这里）

  - 编程结构
    - 顺序、选择、迭代 = 循环

  - 函数
    - 内置函数和自定义函数的使用：
      - 隔离复杂度，代码清晰，代码复用，提高可维护性。
    - 参数传递与返回值：
      - 传递值参与运算，返回值使得下一个函数可以继续运算。
      - 外部提供数据 传入内部函数参与运算
      - 返回值：把数据提供给其他方法

- 编程实践
  - 良好的编程习惯
    - 变量命名：有意义的变量名。
    - 代码注释：让接手的人看懂，提醒自己。
    - 缩进：提高代码可读性。
  - 局部变量和全局变量
    - 作用和作用域：局部变量仅在函数内有效，全局变量在整个程序中有效。
  - 白盒测试（white box testing）
    - 适用性和方法：测试代码内部逻辑。（只有开发人员才能胜任）

- 数据处理
  - 处理有效和无效输入
    - 设计健壮的输入验证机制

- 故障排除和测试
  - 错误识别和解决策略：识别错误、制定策略、执行步骤。

- 技术手册的编写
  - 手册的主要部分
    1. 需求规格: 定义项目或系统需要满足的功能性和非功能性需求，确保开发目标清晰。
        - 有 功能需求和非功能需求 还有 限制条件和使用场景
    
    2. 详细设计: 说明系统实现的技术方案、设计思想和模块分解。
        - 有 系统架构,模块设计,数据库设计,算法设计 
    3. 代码清单: 提供系统实现的核心代码，以便复现或维护。
      - 有 代码结构,核心代码片段,代码规范,编译/运行说明
    4. 测试策略: 描述如何验证系统的正确性、稳定性和性能。
      - 有 测试范围,测试类型,测试工具,测试用例  
    5. 测试日志: 记录测试的实际执行结果及问题，便于追溯和改进。
      - 有 测试记录,测试结果,修复记录,性能指标 

- 伪代码找出bug (逻辑)
  - 通过伪代码分析来识别潜在的bug 的过程，哪些阶段会产生 怎么找(最重要)
  1. 设计阶段 需求不对导致设计不对， 需求对设计不对
  2. 编码阶段 程序的bug 没有遵循设计要求
  3. 测试阶段 输入超出范围
  
    ```
    Initialize total to 0
    Set array to [3, 5, 2, 8, 7, 10, 12]
    Set length to the number of elements array
    Initialize index to 0
    Loop while index is less then length
        If array[index] mod 2 equals 0 then
            Set square to array[index] * array[index]
            Add square to total
        End If
        Increment index by 1
    End Loop
    Display total

    mod 2 是看能不能整除2 能就是偶数 是偶数就会算她的平方然后添加进square然后square被加进total，循环结束之后会输出所有偶数的平方和
    ```

## 职业道德 (Professionalism and Ethics in Computing) 
- 法律与法规（英国为主）
  - 版权，设计和专利法
    - 版权法：保护创作性表达（文学、艺术作品等）。
    - 设计法：保护外观设计（工业产品、图案、装饰设计等）。
    - 专利法：保护技术发明和创新（新产品、新工艺等）。

  - 数据保护法
    - 个人数据处理和储存的法律要求
      1. 数据收集需合法、透明，并取得用户同意。
      2. 数据仅限于特定目的，不得滥用或超范围使用。
      3. 实施技术和组织措施，确保数据安全与隐私保护。
    
    - 数据保留和数据准确性的重要性
      1. 数据保留：仅在必要时间内存储数据，超期应安全删除。
      2. 数据准确性：确保数据完整、最新，避免误导或错误影响决策。
  
  - 消费者保护法
    - 电子商务中的消费者权利和公司的义务(保护消费者)
        1. 知情权：消费者有权了解商品信息、价格、退换政策等。
        2. 选择权：自由选择商品或服务，无强制消费。
        3. 安全权：享有购买安全合规商品的保障。
        4. 隐私权：个人数据受法律保护，不得非法收集或滥用。
        5. 售后权：享有合理退换货及售后服务的保障。
        6. 提供清晰、准确的信息，杜绝虚假宣传。
        7. 确保支付安全，保护消费者个人信息。
        8. 履行合同，及时发货并提供售后服务。
        9. 遵守退换货政策，按承诺解决纠纷。

- 职业道德与行为
  - 职业协会与认证
    - 加入之后他们可以提供什么优势和服务
      1. 专业网络：拓展行业人脉，与同行交流合作。
      2. 技能提升：提供培训、研讨会和持续教育机会。
      3. 行业资源：获取最新趋势、研究报告和工具支持。
      4. 职业认证：提升专业形象和就业竞争力。
      5. 政策影响：参与行业标准制定，增强话语权。
      6. 求职支持：提供招聘信息、职业指导和推荐机会。
  
  - 职业行为守则
    - 专业机构的成员应按照专业机构的规定行事
    - 要求
      - 专业机构成员需遵守诚信、公正、保密等原则。
      - 遵循专业机构的规定，维护行业声誉与标准。
      - 遇到利益冲突时，**优先保护客户和公众利益**。

  - 使用政策和安全
    - 可接受使用政策(Acceptable use policy.AUP)和计算机硬件软件的安全管理
      - 可接受使用政策 (AUP)
        1. 明确用户在使用组织资源（网络、设备等）时的行为准则。
        2. 禁止非法、滥用或未经授权的使用行为。
        
      - 计算机硬件软件的安全管理
        1. 定期更新与补丁，防范安全漏洞。
        2. 实施访问控制，确保权限分配合理。
        3. 数据备份与加密，防止信息泄露或丢失。

- 计算机领域职业及机构 
  - 机构
    - 英国应用软件开发者协会 (BASDA) 软件开发工程师
    - 国际电器与电子工程师协会 (IEEE) 人工智能工程师
    - 美国计算机学会 (ACM) 计算机科学研究员

- 计算机犯罪
  - 未授权的软件复制
    - 法律后果和公司策略
      - 法律后果
        1. 侵犯版权，可能面临罚款、刑事诉讼或赔偿责任。
        2. 企业可能失去信任，影响声誉和合作关系。
      - 公司策略
        1. 制定并实施软件许可合规政策。
        2. 定期审计软件使用，禁止盗版。
        3. 提供合法软件和员工培训。
  - 安全与保密性
    - 处理敏感数据防止数据泄露方法
      - 数据加密：传输与存储时加密保护。
      - 访问控制：限制敏感数据的访问权限。
      - 定期备份：防止数据丢失或篡改。
      - 网络安全措施：使用防火墙、反病毒软件等保护系统。
      - 员工培训：提高安全意识，防范钓鱼攻击和内部泄露。

# 故障诊断
- 常见系统问提
  - 系统性能问题 (System Performance Issues)
    - 磁盘碎片整理、交换文件调整、进程管理
      - 磁盘碎片整理：优化磁盘数据存储，提升读取速度。
      - 交换文件调整：根据内存需求配置适当大小的虚拟内存。
      - 进程管理：终止无响应或占用资源过多的进程。

  - 解决电脑慢
    - 原因
      - 硬件太老(更新)
      - 软件
        - 硬件驱动版本太老 (更新)
        - 后台程序太多 (关进程)
        - 系统盘文件快满了(没有临时文件存放空间) (删文件)
        - 中毒 (杀毒)
        - windows更新变卡(版本不兼容硬件,软件) (降版本)

 - 虚拟内存中的 Swap
    - 定义：当计算机的物理内存（RAM）不足时，操作系统会将不活跃的内存页（内存块）临时存储到硬盘上的**交换文件（swap file）或交换分区（swap partition）**中。这是为了释放内存供当前活跃的进程使用。
    - 作用：它帮助系统在内存资源有限的情况下继续运行，但由于硬盘读写速度比内存慢，因此频繁的交换操作可能导致性能下降。

