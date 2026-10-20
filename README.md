# HanziDict — General Standard Chinese Character Dataset (Chinese–English)

Open data for the **8,105 characters** of 《通用规范汉字表》 *General Standard Chinese
Character Table* (State Council of the PRC, 2013): character forms, readings, structural
attributes, traditional→variant→simplified mappings, and **Chinese–English definitions**.

**Source:** this is a periodic export of the character (字) layer of **[hanzidict.org](https://hanzidict.org)**.
Data is maintained on the website first; corrections are merged into this repository in the
next release. (Only this dataset is open — the website's own source code is not.)

---

## Contents

| File | Rows | What it is |
|---|---|---|
| [`data/hanzidict-characters.json`](data/hanzidict-characters.json) | 8,105 | **Recommended.** Nested: character → readings → senses |
| [`data/characters.csv`](data/characters.csv) | 8,105 | The standard character list: number, level, radical, strokes, stroke order, HSK level |
| [`data/char_pronunciations.csv`](data/char_pronunciations.csv) | 9,723 | Readings, one row per reading |
| [`data/char_aliases.csv`](data/char_aliases.csv) | 3,597 | Traditional / variant character → standard simplified character |
| [`data/glosses.csv`](data/glosses.csv) | 50,499 | Definitions: Chinese text + English translation, with the `source` of every row |

Encoding: UTF-8 (no BOM), RFC 4180 CSV.

A sense carries: `pos` / `pos_en` (part of speech), `content` (definition, Chinese),
`content_en` (definition, English), `examples` (example words), `source`. Empty fields are
omitted, so check for absence rather than emptiness.

**Use JSON** if you are writing code or feeding a pipeline — it is structured and safe in
Excel (see below). **Use CSV** if you are loading into a database or a dataframe.

> If the CSVs look garbled in Excel: the files have no BOM (import via *Data → From
> Text/CSV* and pick UTF-8), and Excel's default font lacks glyphs for the 196 characters
> outside the Basic Multilingual Plane (e.g. `𬙋`, U+2C64B). Neither is file corruption —
> use the JSON, or a font with CJK Extension coverage.

---

## License

**Character layer** — `characters.csv`, `char_aliases.csv`, `char_pronunciations.csv`:
**factual data from official standards, no license required.** Article 5 of the PRC Copyright
Law excludes such documents (《通用规范汉字表》2013, GF 0025-2021 for HSK levels) from
copyright protection, and facts are not copyrightable. Use freely, no conditions. A citation
is appreciated:

> Character data from 《通用规范汉字表》 (2013), State Council of the People's Republic of China.

**Definition layer** — `glosses.csv` and the `senses` in the JSON: **MIT**, with each row's
`source` telling you where it came from.

| `source` | rows | upstream license |
|---|---|---|
| `zdic(汉典)` | 34,397 | CC0 1.0 (public domain, [zdic.net](https://zdic.net)) |
| `HanziDict` | 16,102 | original work of this project — MIT |

CC0 material may be redistributed under any license, so no row here carries a share-alike
obligation. See [LICENSE](LICENSE) for the full text.

## Deliberately excluded

- **CC-CEDICT senses** — CC BY-SA 4.0 is *share-alike*; including it would force this whole
  dataset under CC BY-SA, so it is filtered out.
- **Senses without an English translation** — this dataset is scoped to Chinese–English.
- Word-level data, example sentences, and stroke-order animations.
- Encoding details (`codepoint`, `gbk`) and the internal `zhengma` attribute.

## Corrections and feedback

Found a mistake? Every character page on hanzidict.org has a feedback form in the page
footer — **"Spotted an error? Tell us"** — no account needed. For example:
<https://hanzidict.org/char/拓>.

Corrections are reviewed on the website, then merged here in the next release. The issue
tracker here is not monitored for data errors.

## Credits

- 《通用规范汉字表》 (2013), State Council of the PRC — character set, levels, numbering
- GF 0025-2021 《国际中文教育中文水平等级标准》 — HSK levels
- [pinyin-pro](https://github.com/zh-lx/pinyin-pro) (MIT) — readings
- [zdic.net / 汉典](https://zdic.net) (CC0 1.0) — Chinese definitions
- Maintained by [hanzidict.org](https://hanzidict.org)

## Version

- Data snapshot: **2026-10-20**

---

## 中文简介

本仓库是**通用汉字中英词典数据集**——中国《通用规范汉字表》（2013，国务院发布）**全部
8,105 个规范汉字**的开源数据集，由 **[hanzidict.org](https://hanzidict.org)** 定期导出，
包含字表、读音、结构属性、简繁/异体映射，以及带英文翻译的中文释义。

- **推荐格式** `data/hanzidict-characters.json`：一个字一条记录，属性 → 读音 → 义项逐层嵌套。
- **许可**：字表层（字表 / 读音 / 别名）是官方标准中的事实性数据，**无需任何许可标注**，
  可自由使用；释义层（`glosses.csv`）为 **MIT**（34,397 条来自汉典 zdic.net，CC0 1.0 公有领域；
  16,102 条为本项目原创），逐行只用 `source` 标明出处，不含任何 share-alike 义务。
  本站**网站源码不开源**，仅数据集开源。
- **数据错误反馈**：请到 hanzidict.org 对应字/词页的页脚「Spotted an error? Tell us」表单提交
  （无需注册）。更正会在网站上先行修订，并**定期合并发布**到本仓库的新版本中。
