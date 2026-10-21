# 化学 · 立项说明与总纲

立项日期：2026-10-20。本类是「领域学习谱系」五类中的第五类、也是收尾一类，按《分类总纲》的推进顺序开工：量化交易、健康与长寿、医药与药物研发、生物学之后接化学。它在五类里最上游——分子这一层弄明白了，医药类的药物分子、生物类的结构层才有根。本文件定本类的总纲：收什么、不收什么、跟既有类怎么分工、经典材料有哪些。


支持与更多：[GitHub Sponsors](https://github.com/sponsors/Ezra-Zhao) · [Gumroad — 我在用的模板与工作簿](https://ezraflow28.gumroad.com) · [Ko-fi](https://ko-fi.com/ezra777zhao)

## 一、本类总纲

### 收录范围（照《分类总纲》定版）

收三类东西：

1. **计算化学与化学信息学的开源工具**：分子表示与处理（SMILES、指纹、描述符）、格式转换、分子建模与可视化、轨迹分析——即「化学数据在计算机里怎么存、怎么算」这一层的公共基础设施。
2. **分子模拟与量子化学软件**：经典分子动力学（力场 MD）、第一性原理/DFT 程序、半经验方法、机器学习势函数——按精度与尺度分层收：电子结构（量子化学）→ 原子尺度模拟（MD）→ 分析与可视化。
3. **公开化学数据库与开放教材**：PubChem、NIST Chemistry WebBook、晶体学开放数据库（COD）、Materials Project 等开放数据体系的定位与口径；OpenStax 等开放教材与公认经典教材的名目。

### 不收什么（红线，长期有效）

- **不收危险化学品合成的操作细节**——具体合成路线、制备步骤、提纯与放大工艺，一律不写。本类只讲原理、工具与公开数据，不提供任何可以照着做出危险品的操作信息。
- **不收受管制物质相关内容**——管制药品、爆炸物、化学武器相关前体与制剂的合成、检测规避、获取渠道类内容，整体排除，不设例外。
- 不收纯商业闭源软件的推广性内容（Gaussian、Materials Studio 等商业软件在经典清单里可以作为行业事实提及，但不做导读、不写使用教程）。
- 不收湿实验操作规程（实验室 SOP 类）：本类是计算与数据之学，不教人动手做实验。

这条红线与生物类排除危险病原、医药类排除诊疗建议是同一条纪律：谱系只做理解层与工具层的教育，操作层的高风险内容整体不进。

### 按方法分层收录（批次的组织方式）

1. **化学信息学层**：分子表示、描述符与指纹、格式转换（RDKit、Open Babel 等）——化学数据的地基。
2. **结构与材料层**：晶体与分子结构对象、材料数据库接口（pymatgen 等），与生物类的结构生物学工具分工见第二节。
3. **量子化学层**：Hartree–Fock、DFT、后 HF 方法的程序实现（Psi4、PySCF、CP2K 等），外加经典教材与里程碑论文。
4. **半经验层**：紧束缚与半经验方法（xtb 等）——精度与速度之间的折中层，也是大体系量子化学的实用入口。
5. **分子动力学层**：经典力场 MD 引擎（LAMMPS、OpenMM 等）与机器学习势（DeePMD-kit 等）。
6. **分析与可视化层**：轨迹分析（MDAnalysis 等）与分子编辑/可视化（Avogadro 等）。
7. **开放数据层**：PubChem、NIST WebBook、COD、Materials Project 等数据体系（经典清单先列名目，导读随后续批次展开）。

### 学习路线（草案，随批次细化为正式路线图）

- 阶段 0 准备：普通化学骨架先立起来——原子结构、化学键、分子几何、热力学与动力学的基本语言（开放教材走 OpenStax《Chemistry 2e》，在版教材对照 Atkins）。这一阶段不碰软件。
- 阶段 1 分子进计算机：SMILES 与分子图、二维/三维结构、描述符与指纹——用 RDKit 把「分子变成数据」这件事做一遍（工具本体在本类，药物场景的应用见医药类）。
- 阶段 2 量子化学：从 Hartree–Fock 到 DFT，读 Hohenberg–Kohn 与 Kohn–Sham 两篇原文的导读，用 Psi4 或 PySCF 算一个小分子的能量与几何优化，理解「基组」和「泛函」两个词到底在选什么。
- 阶段 3 分子动力学：力场、系综、积分步长，用 OpenMM 或 LAMMPS 跑一段短轨迹，再用 MDAnalysis 分析——回头对照 Frenkel & Smit 讲算法的那几章。
- 阶段 4 尺度与取舍：半经验（xtb）与机器学习势（DeePMD-kit）为什么存在——精度、体系大小、算力三者的账要会算。学完这一阶段，应该能对一个给定的化学问题说出该用哪一层方法、大概贵在哪里。

## 二、与既有类的关系（分工口径，长期有效）

### 与医药与药物研发类（重叠最容易发生的地方，先把口径钉死）

化学信息学工具是药物研发的日常家伙，两类天然交叠。医药类立项时定的口径是「同一仓两边可以各写一篇、角度不同」；本类在此基础上再收紧一步，避免读者在两个仓里读到两篇口径打架的同题文章：

- **工具本体归本类，药物应用归医药类。** RDKit、Open Babel 这类工具，在本类写「工具本体」：数据结构与算法、表示与描述符体系、在化学数据生态里的位置；医药类写「药物应用」：在筛选、ADMET、管线里的用法。医药类第一批已经先行收了 RDKit（其第一批第 2 条）与 Open Babel（第 4 条），写的是药物研发角度；本类第一批收同两仓的本体条目，并在条目内明确标注医药类应用篇的位置，两边互相回指，不重复展开同一层内容。
- **平台型框架不两边收。** DeepChem 是把化学信息学、量子化学数据与药物 ML 串起来的平台，医药类第一批已收（其第 1 条），本类不再另写，只在化学信息学层的叙述里交叉引用。
- **数据库各表一面。** PubChem 这类体系，医药类经典清单从「药物数据」角度列过；本类在开放数据层从「化学开放数据基础设施」角度立目（与 NIST WebBook、COD 并列），取数工具（如 PubChemPy）归医药类第二批数据库专题，本类不另收客户端。
- **结构编辑器归属待协调的一件**：Ketcher（epam/ketcher）医药类已列为其第二批候选。本类可视化层先收 Avogadro（编辑+可视化+建模一体），Ketcher 等医药类第二批落定后再议，不抢位。

### 与生物学类

- 生物类管序列与组学（基因组、转录组、单细胞）和大分子结构工具链（其第一批收了 AlphaFold、GATK、Galaxy 等）。本类的 pymatgen 一类结构工具面向晶体、材料与小分子结构对象，不进生物大分子的地盘；蛋白质结构预测、结构生物学归生物类与医药类的结构层（PDB、AlphaFold DB 在那两类已立目）。
- 分子动力学这一层两边都要用（生物分子模拟是 MD 的大用户），口径是：引擎本体（OpenMM、LAMMPS）归本类，生物类在自己的路线里回链引用，不另写引擎条目。

### 与其他线

- 本类与量化、长寿两类无直接交叠。方法论上与各类的关系一致：本类供底层知识与工具底料，各应用类回链引用，互不背书、互不重复建设。

## 三、经典学习材料清单（只列名目与出处，本批不展开导读；名目与出处已于 2026-10-20 逐个核对出版社页面、期刊原文与官方站点）

### 教材（只列名目，在版书籍不做全文处理）

- *Atkins' Physical Chemistry*（Peter Atkins、Julio de Paula、James Keeler，Oxford University Press；第 12 版，2023 年）——物理化学的通行权威教材：热力学、量子化学、统计热力学与光谱的本科—研究生主线教材，本类阶段 0 与阶段 2 的对照读物。
- *Molecular Modelling: Principles and Applications*（Andrew R. Leach，Pearson Education；第 2 版，2001 年）——分子建模领域的标准入门教材：力场、能量最小化、分子动力学、构象分析、QSAR 一条线讲下来，是「计算化学工具为什么长这样」的最好背景书。
- *Modern Quantum Chemistry: Introduction to Advanced Electronic Structure Theory*（Attila Szabo、Neil S. Ostlund，McGraw-Hill 1982 年初版，Dover 1996 年重印）——电子结构理论的经典教材，Hartree–Fock 与后 HF 方法的数学骨架，学量子化学程序之前先读它。
- *Introduction to Computational Chemistry*（Frank Jensen，Wiley；第 3 版，2017 年）——计算化学方法总览：基组、泛函、半经验、力场各方法的适用边界与坑，选方法时翻它。
- *Essentials of Computational Chemistry: Theories and Models*（Christopher J. Cramer，Wiley；第 2 版，2004 年）——侧重「方法在化学问题上怎么用」的教材，与 Jensen 互补。

### 分子模拟专著

- *Understanding Molecular Simulation: From Algorithms to Applications*（Daan Frenkel、Berend Smit，Academic Press；第 3 版，2023 年）——分子模拟的算法圣经：Monte Carlo 与 MD 的统计力学根基、自由能计算、罕见事件方法，本类阶段 3 的主对照书。
- *Computer Simulation of Liquids*（Michael P. Allen、Dominic J. Tildesley，Oxford University Press；第 2 版，2017 年）——液体模拟的经典：周期性边界、长程作用处理、系综实现的细节出处。

### 里程碑论文（量子化学与 DFT 的地基，全文在期刊，本类只做导读）

- **Hohenberg–Kohn 定理**：P. Hohenberg & W. Kohn, "Inhomogeneous Electron Gas", *Physical Review* 136(3B): B864–B871, 1964——证明基态电子密度决定体系一切性质，密度泛函理论（DFT）的存在性地基。
- **Kohn–Sham 方程**：W. Kohn & L. J. Sham, "Self-Consistent Equations Including Exchange and Correlation Effects", *Physical Review* 140(4A): A1133–A1138, 1965——把 DFT 变成可计算方程的那篇，现代所有 DFT 程序的起点。Kohn 因此获 1998 年诺贝尔化学奖。
- **B3LYP 的两块拼图**：A. D. Becke, "Density-functional thermochemistry. III. The role of exact exchange", *Journal of Chemical Physics* 98(7): 5648–5652, 1993（三参数杂化泛函）；C. Lee, W. Yang & R. G. Parr, "Development of the Colle-Salvetti correlation-energy formula into a functional of the electron density", *Physical Review B* 37(2): 785–789, 1988（LYP 相关泛函）。
- **B3LYP 的落地定义**：P. J. Stephens、F. J. Devlin、C. F. Chabalowski & M. J. Frisch, "Ab Initio Calculation of Vibrational Absorption and Circular Dichroism Spectra Using Density Functional Force Fields", *Journal of Physical Chemistry* 98(45): 11623–11627, 1994——把 Becke 三参数与 LYP 组合成今天各程序里那个「B3LYP」的具体配方，是化学界引用量最高的泛函定义之一。
- **Car–Parrinello 方法**：R. Car & M. Parrinello, "Unified Approach for Molecular Dynamics and Density-Functional Theory", *Physical Review Letters* 55(22): 2471–2474, 1985——第一性原理分子动力学的开端，本类 CP2K 一类程序的思想源头。

### 公开化学数据体系（官方，一手来源）

- **PubChem**（美国 NIH 旗下 NCBI/NLM 运营，2004 年上线）：全球最大的开放化学信息库，化合物（Compound）、物质（Substance）与生物测定（BioAssay）三大部分；定期更新论文见 Kim et al., *Nucleic Acids Research*。在本谱系里它同时是医药类的药物数据来源，分工见第二节：本类立其「化学开放数据基础设施」的目，药物应用与取数工具归医药类。
- **NIST Chemistry WebBook**（美国国家标准与技术研究院，Standard Reference Database 69）：热化学、质谱、红外与紫外光谱、气相离子能学等实验数据的权威汇编，查一个分子的实验性质先来这里对表。
- **Crystallography Open Database（COD）**（2003 年发起）：开放获取的晶体结构数据库，收有机、无机与金属有机晶体的实验结构，与剑桥结构数据库（CSD，商业）形成开放侧的对应物。
- **Materials Project**（美国劳伦斯伯克利国家实验室牵头）：以高通量 DFT 计算建成的材料性质数据库（形成能、能带、弹性等），数据库论文 Jain et al., *APL Materials* 1: 011002, 2013；本类第一批的 pymatgen 就是它的官方 Python 库——数据体系与工具在同一条线上。

### 开放教材

- *Chemistry 2e*（OpenStax，莱斯大学；2019 年第 2 版，开放许可发布，官方站点免费阅读与下载）：两学期普通化学的完整教材，本类阶段 0 的指定读物——免费、体系完整、习题齐全，是「先把普化骨架立起来」成本最低的路。同系列另有 *Chemistry: Atoms First 2e*（原子优先的编排顺序），二选一即可。

## 四、批次规划

- 第一批（已完成）：按方法分层选的 12 仓导读，见 `第一批-导读.md`。选品与取舍留痕一并写在该文件卷首。
- 第二批（候）：量子化学与模拟的补强专题——NWChem（美国能源部西北太平洋国家实验室的经典高性能量子化学程序，许可证为其自有 ECL 口径，第二批按「经典程序样本」定位收）、输出解析库 cclib、轨迹处理 MDTraj、自由能增强采样 PLUMED、浏览器端可视化 3Dmol.js 等补齐第一批的同层空位。
- 托管在 GitLab 的两位重要成员——GROMACS（分子动力学）与 ASE（原子模拟环境）——GitHub 上只有镜像或没有官方仓，不按「GitHub 仓导读」的体例硬收；第二批视情况以「专题条目」形式处理并注明主仓位置，不让读者误以为它们不存在。
- 经典材料导读（从 Hohenberg–Kohn 与 Kohn–Sham 两篇起）与学习路线图正式版，在项目导读攒到两批后开工，与其他各类的节奏一致。
