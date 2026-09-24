## 专题一：workbench前处理

![图片](http://www.kdocs.cn/api/v3/office/copy/RjRYL25NdG1rcUlrdnVuRVAyZlBVL2dySWVOd0sxUlU3M01zRGVGamtLcGZ1b25zYlp3RGhQWk5aYWVrYVFMdzlqNjBVWDhNUE9KQmloVmVQS2dZQkRFeG4vQW8yWFg5allrOGFGaHVWd3UzSGNHR3FMSVh0NXdHbGpHb0NVa0d6SFdneFA1SmRlYnVVbUw4S09sdkRNbmlHNVdkbzVWYTFxd20reTlaWEhXMFJDR0RmM1FudW93QjMwSEFtbXFMSFhQbmJFUFp0WFpaZkU0YVNZRHZOQ3YyZE8wQUdjYjFBVDdvaGE2YUlMSy9FM3dMZVgzMGRBVUJIY2dRUVBhSTBiWGJzdUVCY3BzPQ==/attach/object/6YTPSCZKABQBU?&kso_type=image&kso_extra=eyJ0eXBlIjoiaW1hZ2UiLCJpZCI6IjZZVFBTQ1pLQUJRQlUiLCJvd25lciI6IjU2MTkwNzQzMzEyOSIsInJvdGF0ZSI6MCwic3RvcmFnZSI6ImJhc2UiLCJ3aWR0aCI6MTU4NiwiaGVpZ2h0Ijo5OTJ9)

1. ### workbench基础

   单个分析系统结构：

   ![图片](http://www.kdocs.cn/api/v3/office/copy/RjRYL25NdG1rcUlrdnVuRVAyZlBVL2dySWVOd0sxUlU3M01zRGVGamtLcGZ1b25zYlp3RGhQWk5aYWVrYVFMdzlqNjBVWDhNUE9KQmloVmVQS2dZQkRFeG4vQW8yWFg5allrOGFGaHVWd3UzSGNHR3FMSVh0NXdHbGpHb0NVa0d6SFdneFA1SmRlYnVVbUw4S09sdkRNbmlHNVdkbzVWYTFxd20reTlaWEhXMFJDR0RmM1FudW93QjMwSEFtbXFMSFhQbmJFUFp0WFpaZkU0YVNZRHZOQ3YyZE8wQUdjYjFBVDdvaGE2YUlMSy9FM3dMZVgzMGRBVUJIY2dRUVBhSTBiWGJzdUVCY3BzPQ==/attach/object/HOQQADBKACQAW?&kso_type=image&kso_extra=eyJ0eXBlIjoiaW1hZ2UiLCJpZCI6IkhPUVFBREJLQUNRQVciLCJvd25lciI6IjU2MTkwNzQzMzEyOSIsInJvdGF0ZSI6MCwic3RvcmFnZSI6ImJhc2UiLCJ3aWR0aCI6NzY5LCJoZWlnaHQiOjU4fQ)

   数据共享：数据在两个模块之间共享，意味着实际上只有一个底层数据对象同时服务于两个模块。变更 单元会立即影响对方，因为它们本质上是数据相同。共享连接用方形连接器表示

   ![图片](http://www.kdocs.cn/api/v3/office/copy/RjRYL25NdG1rcUlrdnVuRVAyZlBVL2dySWVOd0sxUlU3M01zRGVGamtLcGZ1b25zYlp3RGhQWk5aYWVrYVFMdzlqNjBVWDhNUE9KQmloVmVQS2dZQkRFeG4vQW8yWFg5allrOGFGaHVWd3UzSGNHR3FMSVh0NXdHbGpHb0NVa0d6SFdneFA1SmRlYnVVbUw4S09sdkRNbmlHNVdkbzVWYTFxd20reTlaWEhXMFJDR0RmM1FudW93QjMwSEFtbXFMSFhQbmJFUFp0WFpaZkU0YVNZRHZOQ3YyZE8wQUdjYjFBVDdvaGE2YUlMSy9FM3dMZVgzMGRBVUJIY2dRUVBhSTBiWGJzdUVCY3BzPQ==/attach/object/J2WQGDBKACQGY?&kso_type=image&kso_extra=eyJ0eXBlIjoiaW1hZ2UiLCJpZCI6IkoyV1FHREJLQUNRR1kiLCJvd25lciI6IjU2MTkwNzQzMzEyOSIsInJvdGF0ZSI6MCwic3RvcmFnZSI6ImJhc2UiLCJ3aWR0aCI6MzgzLCJoZWlnaHQiOjE1OH0)

   数据提供：上游模块向下游模块提供输入数据。变更上游单元将标记为需要刷新。 连接用圆形连接器表示，双方并不是同一个模型对象。

   ![图片](http://www.kdocs.cn/api/v3/office/copy/RjRYL25NdG1rcUlrdnVuRVAyZlBVL2dySWVOd0sxUlU3M01zRGVGamtLcGZ1b25zYlp3RGhQWk5aYWVrYVFMdzlqNjBVWDhNUE9KQmloVmVQS2dZQkRFeG4vQW8yWFg5allrOGFGaHVWd3UzSGNHR3FMSVh0NXdHbGpHb0NVa0d6SFdneFA1SmRlYnVVbUw4S09sdkRNbmlHNVdkbzVWYTFxd20reTlaWEhXMFJDR0RmM1FudW93QjMwSEFtbXFMSFhQbmJFUFp0WFpaZkU0YVNZRHZOQ3YyZE8wQUdjYjFBVDdvaGE2YUlMSy9FM3dMZVgzMGRBVUJIY2dRUVBhSTBiWGJzdUVCY3BzPQ==/attach/object/6PCQMDBKAAACS?&kso_type=image&kso_extra=eyJ0eXBlIjoiaW1hZ2UiLCJpZCI6IjZQQ1FNREJLQUFBQ1MiLCJvd25lciI6IjU2MTkwNzQzMzEyOSIsInJvdGF0ZSI6MCwic3RvcmFnZSI6ImJhc2UiLCJ3aWR0aCI6NDE2LCJoZWlnaHQiOjExMX0)

   创建数据共享的方式：

   1、拖动新的模块到原有模块对应位置，例如，原有静力学分析，课程Toolbox拖动模态到静力学几何上

   ![图片](http://www.kdocs.cn/api/v3/office/copy/RjRYL25NdG1rcUlrdnVuRVAyZlBVL2dySWVOd0sxUlU3M01zRGVGamtLcGZ1b25zYlp3RGhQWk5aYWVrYVFMdzlqNjBVWDhNUE9KQmloVmVQS2dZQkRFeG4vQW8yWFg5allrOGFGaHVWd3UzSGNHR3FMSVh0NXdHbGpHb0NVa0d6SFdneFA1SmRlYnVVbUw4S09sdkRNbmlHNVdkbzVWYTFxd20reTlaWEhXMFJDR0RmM1FudW93QjMwSEFtbXFMSFhQbmJFUFp0WFpaZkU0YVNZRHZOQ3YyZE8wQUdjYjFBVDdvaGE2YUlMSy9FM3dMZVgzMGRBVUJIY2dRUVBhSTBiWGJzdUVCY3BzPQ==/attach/object/3NNWODBKADQDY?&kso_type=image&kso_extra=eyJ0eXBlIjoiaW1hZ2UiLCJpZCI6IjNOTldPREJLQURRRFkiLCJvd25lciI6IjU2MTkwNzQzMzEyOSIsInJvdGF0ZSI6MCwic3RvcmFnZSI6ImJhc2UiLCJ3aWR0aCI6NTE5LCJoZWlnaHQiOjMxMH0)

   2、Geometry右键创建下游系统

   ![图片](http://www.kdocs.cn/api/v3/office/copy/RjRYL25NdG1rcUlrdnVuRVAyZlBVL2dySWVOd0sxUlU3M01zRGVGamtLcGZ1b25zYlp3RGhQWk5aYWVrYVFMdzlqNjBVWDhNUE9KQmloVmVQS2dZQkRFeG4vQW8yWFg5allrOGFGaHVWd3UzSGNHR3FMSVh0NXdHbGpHb0NVa0d6SFdneFA1SmRlYnVVbUw4S09sdkRNbmlHNVdkbzVWYTFxd20reTlaWEhXMFJDR0RmM1FudW93QjMwSEFtbXFMSFhQbmJFUFp0WFpaZkU0YVNZRHZOQ3YyZE8wQUdjYjFBVDdvaGE2YUlMSy9FM3dMZVgzMGRBVUJIY2dRUVBhSTBiWGJzdUVCY3BzPQ==/attach/object/ISMGQDBKAAAGS?&kso_type=image&kso_extra=eyJ0eXBlIjoiaW1hZ2UiLCJpZCI6IklTTUdRREJLQUFBR1MiLCJvd25lciI6IjU2MTkwNzQzMzEyOSIsInJvdGF0ZSI6MCwic3RvcmFnZSI6ImJhc2UiLCJ3aWR0aCI6NTIyLCJoZWlnaHQiOjM3MX0)

   3、两分析系统直接对应拖动连接

   **注意：**不能在两个已经建立好的分析系统之间事后创建Model共享；通常应从第一个系统的Model单元格直接生成第二个连接系统，如果已经分别建立了两个系统，最稳妥的做法通常是删除或保留其中一个下游系统，然后重新从上游Model生成连接系统。

   创建数据提供与共享类似，用于传递Solution分析结果，是把上游的计算结果转换为下游分析的载荷、初始条件、或预应力状态。

2. ### 几何前处理

   1. spaceclaim和discovery

      ![图片](http://www.kdocs.cn/api/v3/office/copy/RjRYL25NdG1rcUlrdnVuRVAyZlBVL2dySWVOd0sxUlU3M01zRGVGamtLcGZ1b25zYlp3RGhQWk5aYWVrYVFMdzlqNjBVWDhNUE9KQmloVmVQS2dZQkRFeG4vQW8yWFg5allrOGFGaHVWd3UzSGNHR3FMSVh0NXdHbGpHb0NVa0d6SFdneFA1SmRlYnVVbUw4S09sdkRNbmlHNVdkbzVWYTFxd20reTlaWEhXMFJDR0RmM1FudW93QjMwSEFtbXFMSFhQbmJFUFp0WFpaZkU0YVNZRHZOQ3YyZE8wQUdjYjFBVDdvaGE2YUlMSy9FM3dMZVgzMGRBVUJIY2dRUVBhSTBiWGJzdUVCY3BzPQ==/attach/object/CJONYERKABAH6?&kso_type=image&kso_extra=eyJ0eXBlIjoiaW1hZ2UiLCJpZCI6IkNKT05ZRVJLQUJBSDYiLCJvd25lciI6IjU2MTkwNzQzMzEyOSIsInJvdGF0ZSI6MCwic3RvcmFnZSI6ImJhc2UiLCJ3aWR0aCI6NzUxLCJoZWlnaHQiOjYzMH0)

   2. Ansys Discovery

      **一 主要功能**

      |**功能**|**说明**|
      |---|---|
      |**结构分析**|支持静态和动态结构分析，可快速观察变形、应力及不同振型，并估计固有频率和共振风险。|
      |**流体分析**|可探索内部流动和外部流动，观察速度、压力和流线等结果。需要更详细或更高精度分析时，可进一步使用 Refine 工作流或转入 Ansys Fluent。|
      |**热分析**|可分析热传导、对流和温度分布，并支持共轭传热等热流体问题，用于评估产品的热性能。|
      |**拓扑优化**|提供交互式拓扑优化工具，可根据载荷、约束、保留区域和制造条件调整材料分布，适用于结构减重和刚度提升。|
      |**电磁分析**|可在进入 Ansys HFSS 详细研究前评估初步高频电磁概念，例如天线布置和位置变化对性能的影响。相关能力取决于 Discovery 授权等级。|
      |**设计和几何建模**|采用直接建模技术，可快速建立概念模型、零件和装配体，并能打开、修复和编辑多种 CAD 文件。|
      |**仿真模型准备**|可修改、简化、优化和参数化 CAD 模型，删除无关小特征，修复几何缺陷并建立仿真所需的几何分区，从而降低网格复杂度和求解成本。|

      
      **二 主要优势**

      **• 即时仿真：**通过 GPU 加速和快速求解能力，在修改几何、材料或边界条件后迅速更新结果，使工程师能够在设计早期迭代更多方案。

      **• 易用性强：**界面和工作流相对直观，将交互式建模与仿真设置结合，降低非专业仿真用户的入门门槛。

      **• 兼顾快速探索与高精度验证：**Explore 适合快速判断设计趋势，Refine 适合进一步提高求解精度；最终方案还可传递至 Mechanical、Fluent 或 HFSS 进行专业验证。

      **• 多物理场集成：**能够在统一环境中处理结构、热、流体及部分电磁问题，减少不同软件之间反复转换数据和重建模型的工作量。

      **• CAD 兼容性与模型准备能力：**能够导入和编辑多种 CAD 格式，并通过几何修复、简化、参数化和直接建模工具缩短仿真准备时间。

3. ### 网格划分

   

## case 1 机床主轴模态、随机振动仿真

模态仿真研究内容：结构的固有振动特性，即结构在没有持续外部激励时，最容易以哪些频率和形态发生振动。其核心输出是固有频率和对应的振型，可用于识别共振风险，并为谐响应、随机振动和瞬态动力学分析提供基础。

### 主要研究内容：

- **固有频率分析**：计算结构前若干阶固有频率，确定容易发生共振的频率范围。

- **振型分析**：观察各阶模态下结构的弯曲、扭转、拉伸或局部振动形式。

- **薄弱位置识别**：根据振型中的高位移区域，判断潜在的振动敏感区和连接薄弱位置。

- **结构参数影响**：研究材料、质量、刚度、尺寸、连接方式和边界条件对模态特性的影响。

- **结构优化**：通过改变厚度、增加加强筋、调整支撑或降低局部质量，使固有频率避开工作激励频率。

- **后续动力学分析**：将模态结果传递给谐响应、响应谱、随机振动或瞬态结构分析。

### 基本流程：

![图片](http://www.kdocs.cn/api/v3/office/copy/RjRYL25NdG1rcUlrdnVuRVAyZlBVL2dySWVOd0sxUlU3M01zRGVGamtLcGZ1b25zYlp3RGhQWk5aYWVrYVFMdzlqNjBVWDhNUE9KQmloVmVQS2dZQkRFeG4vQW8yWFg5allrOGFGaHVWd3UzSGNHR3FMSVh0NXdHbGpHb0NVa0d6SFdneFA1SmRlYnVVbUw4S09sdkRNbmlHNVdkbzVWYTFxd20reTlaWEhXMFJDR0RmM1FudW93QjMwSEFtbXFMSFhQbmJFUFp0WFpaZkU0YVNZRHZOQ3YyZE8wQUdjYjFBVDdvaGE2YUlMSy9FM3dMZVgzMGRBVUJIY2dRUVBhSTBiWGJzdUVCY3BzPQ==/attach/object/6IOPDTRJABAA2?&kso_type=image&kso_extra=eyJ0eXBlIjoiaW1hZ2UiLCJpZCI6IjZJT1BEVFJKQUJBQTIiLCJvd25lciI6IjU2MTkwNzQzMzEyOSIsInJvdGF0ZSI6MCwic3RvcmFnZSI6ImJhc2UiLCJ3aWR0aCI6NzY4LCJoZWlnaHQiOjM2NH0)

### 常见模态分析类型：

![图片](http://www.kdocs.cn/api/v3/office/copy/RjRYL25NdG1rcUlrdnVuRVAyZlBVL2dySWVOd0sxUlU3M01zRGVGamtLcGZ1b25zYlp3RGhQWk5aYWVrYVFMdzlqNjBVWDhNUE9KQmloVmVQS2dZQkRFeG4vQW8yWFg5allrOGFGaHVWd3UzSGNHR3FMSVh0NXdHbGpHb0NVa0d6SFdneFA1SmRlYnVVbUw4S09sdkRNbmlHNVdkbzVWYTFxd20reTlaWEhXMFJDR0RmM1FudW93QjMwSEFtbXFMSFhQbmJFUFp0WFpaZkU0YVNZRHZOQ3YyZE8wQUdjYjFBVDdvaGE2YUlMSy9FM3dMZVgzMGRBVUJIY2dRUVBhSTBiWGJzdUVCY3BzPQ==/attach/object/D3P6TTRJADQFS?&kso_type=image&kso_extra=eyJ0eXBlIjoiaW1hZ2UiLCJpZCI6IkQzUDZUVFJKQURRRlMiLCJvd25lciI6IjU2MTkwNzQzMzEyOSIsInJvdGF0ZSI6MCwic3RvcmFnZSI6ImJhc2UiLCJ3aWR0aCI6NzAxLCJoZWlnaHQiOjI5Mn0)



