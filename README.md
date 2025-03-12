# datasets-pigs
Datasets for pig re-identification and related tasks

There are two datasets in total for the project:
1. FaroPigReID-33
   This dataset is created for pig re-identification task, and it consists of 33 identities of mature pigs with around 300 to 4000 masks per individual.

2. FaroPigSeg
   This dataset is created for pig instance segmentation task, and it consists of 1518 images annotated with masks. The images covers 3 production cycles (one year) of a commercial wean to finish farm.

We are now in the process of some legal paperwork for making the datasets public and will release the datasets as soon as possible...

# 数据集名称

简短描述数据集的内容和用途。

## 数据集概述

- **数据集名称**: 数据集名称
- **作者**: 作者姓名或组织
- **发布日期**: YYYY-MM-DD
- **版本**: 版本号 (如 v1.0)
- **许可证**: 数据集许可证 (如 CC BY 4.0)
- **数据集大小**: 数据集大小 (如 1GB)
- **文件格式**: 文件格式 (如 CSV, JSON, Parquet)

## 数据集描述

详细描述数据集的内容、来源、收集方法和用途。

### 数据来源

说明数据来源，如公开数据库、实验数据或网络爬取。

### 数据收集方法

描述数据收集的过程和工具。

### 数据结构

列出数据集包含的文件及其结构：

- `data/`: 包含所有数据文件
  - `file1.csv`: 描述文件内容
  - `file2.json`: 描述文件内容
- `docs/`: 包含相关文档
  - `documentation.pdf`: 详细文档

## 数据字段说明

列出数据集中的字段及其含义：

| 字段名 | 类型 | 描述 |
|--------|------|------|
| field1 | 类型 | 描述 |
| field2 | 类型 | 描述 |

## 使用示例

提供使用数据集的代码示例：

```python
import pandas as pd

# 加载数据集
data = pd.read_csv('data/file1.csv')

# 显示前几行
print(data.head())
