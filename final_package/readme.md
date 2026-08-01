# COMP9727 Final Notebook — Colab package

请把整个 `COMP9727_Final_Colab_Package` 文件夹上传到 Google Drive 的 `MyDrive` 顶层。不要只上传 notebook。

预期上传后的结构：

```text
MyDrive/
└── COMP9727_Final_Colab_Package/
    ├── Kindle_Recommender_Final_Submission_Colab.ipynb
    ├── processed_kindle.zip
    ├── cache/
    │   ├── kindle_meta_summary_full.json
    │   └── kindle_review_summary_full.json
    └── outputs/
        ├── collaborative_model.pt
        ├── gru4rec_best.pt
        └── 若干已有结果 CSV
```

## 在 Colab 中运行

1. 在 Google Drive 中双击 `Kindle_Recommender_Final_Submission_Colab.ipynb`，选择用 Google Colab 打开。
2. 建议选择 GPU：`Runtime` → `Change runtime type` → `T4 GPU`。
3. 选择 `Runtime` → `Run all`。
4. 首个代码单元会请求挂载 Google Drive。授权后，它会自动定位项目包、首次解压 `processed_kindle.zip`、校验 15 个数据文件和两个模型 checkpoint，并切换工作目录。
5. 首次解压后会出现 `processed_kindle/` 文件夹。请保留该文件夹，之后重跑不会重复解压。

所有新结果会保存在此项目包的 `outputs/` 中。不要把 notebook 单独移动到其他文件夹，也不要重命名项目包文件夹，除非同步修改首个 bootstrap 单元中的 `PACKAGE_NAME`。

## 为什么不包含原始 JSONL

默认 `RUN_FULL_PREPROCESSING = False`，运行使用已经生成的 `processed_kindle/` 数据，因此不需要数 GB 的原始 Amazon JSONL 文件。EDA 使用 `cache/` 中的两个汇总文件，也不需要 `proj1/Kindle_Store.jsonl.gz` 和 `proj1/meta_Kindle_Store.jsonl.gz`。

若把 `RUN_FULL_PREPROCESSING` 改为 `True`，则这个精简包不够，还必须另行加入未压缩的 `Kindle_Store.jsonl` 和 `meta_Kindle_Store.jsonl`。
