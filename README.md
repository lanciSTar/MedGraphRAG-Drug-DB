# MedGraphRAG Drug DB

本仓库是从 MedGraphRAG 项目中独立出来的药品数据目录，用于在 GitHub 上分享药品词典、药品分类和清洗后的药品名数据。

## 目录内容

| 文件 | 说明 |
|---|---|
| `drug_db.json` | 药典网爬取并整理后的药品说明书与药物相互作用数据 |
| `drug_db_v2.json` | 清洗后的药品名称与结构化数据 |
| `drug_categories_chinese.json` | 中药用途分类映射 |
| `drug_categories_western.json` | 化学药用途分类映射 |

## 数据用途

这些数据用于医疗问诊系统中的：

- 药品实体识别
- 药品说明书查询
- 药物相互作用检查
- 药品类别关系展开

## 数据结构示例

`drug_db.json` 的顶层包含 `drugs` 和 `interactions` 两个字段。单个药品对象的结构如下：

```json
{
  "drugs": {
    "氨力农注射液": {
      "indication": "适用于对洋地黄、利尿剂、血管扩张剂治疗无效或效果欠佳的各种原因引起的急、慢性顽固性充血性心力衰竭。",
      "contraindications": [
        "严重低血压"
      ],
      "warnings": "1. 氨力农在溶媒中成盐速度较慢…… 长期口服副作用大，口服制剂已不再应用，只限用于短期静脉应用。",
      "composition": "氨力农",
      "dosage": "",
      "adverse_reactions": "可有胃肠反应、血小板减少、室性心律失常、低血压及肝肾功能损害等。",
      "drug_interactions": "1. 与丙吡胺同用可导致血压过低。2. 与硝酸酯类合用有相加效用。",
      "storage": "遮光，密闭保存。",
      "validity": "",
      "approval_numbers": [
        "氨力农注射液批准文号及生产厂家",
        "氨力农注射液 国药准字H10960328 10ml:50mg 扬州中宝药业股份有限公司"
      ],
      "manufacturers": [
        "氨力农注射液 国药准字H10960328 10ml:50mg 扬州中宝药业股份有限公司"
      ],
      "source": "https://www.yaopinnet.com/huayao/hy34290.htm"
    }
  },
  "interactions": []
}
```

其中 `drug_db_v2.json` 是清洗后的版本，主要对药品名称进行了规范化、去重和剂型拆分。



## 来源说明

原始数据来源为药典网，经项目内爬虫和清洗脚本处理。发布到公开仓库前，请先确认原始数据源的转载、使用和再分发许可。

建议在仓库中保留以下信息：

- 数据来源名称
- 采集日期
- 采集脚本说明
- 是否允许二次分发

## 使用方式

在 MedGraphRAG 项目中，将这些文件放到以下目录：

```text
data/raw/drug_db/
```

系统会通过 `app/config/paths.py` 读取对应路径。

## 免责声明

本项目不提供医疗建议。数据仅供研究、开发和测试使用，不能替代医生面诊或专业医疗机构建议。
