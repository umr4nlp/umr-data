# UMR 3.0 Data Release

## Table of Contents
- [UMR 3.0 Data Release](#umr-20-data-release)
  - [UMR 3.0 Data Parser Tool](#umr-20-data-parser-tool)
    - [Usage](#usage)
    - [Options](#options)
    - [Examples](#examples)
    - [Output Format](#output-format)
  - [UMR 3.0 Data format Description](#umr-20-data-format-description)
    - [Block Structure](#block-structure)
    - [Meta Information](#1-meta-information)
    - [Sentence Information](#2-sentence-information)
    - [Sentence-Level UMR Annotation](#3-sentence-level-umr-annotation)
    - [Alignment Information](#4-alignment-information)
    - [Document-Level Annotation](#5-document-level-annotation)
    - [Language Coverage](#language-coverage)
  - [Statistics Tables Description](#statistics)

## UMR 3.0 Data Parser Tool

The `parse_umr_to_json.py` script extracts content from UMR files and converts it to JSON format. It properly handles the block structure of UMR files, where:

- Files are divided into blocks (sentences) separated by 80 hash signs (`####...####`)
- Each block contains 5 parts separated by single hash signs (`#`):
  1. Meta info (with `::` separators)
  2. Sentence information (index, words, morphemes, etc.)
  3. Sentence level UMR annotation (after `# sentence level graph:`)
  4. Alignment information (after `# alignment:`)
  5. Document level annotation (after `# document level annotation:`)

### Usage

```bash
python parse_umr_to_json.py [options]
```

### Options

- `--root-dir PATH` - Root directory containing language subdirectories (default: "ready_to_release")
- `--output PATH` - Output JSON file path (default: "umr_data.json")
- `--language LANG` - Filter by language (e.g., english, chinese)
- `--partial-conversion` - Only include files with type=partial_conversion in meta information
- `--no-partial-conversion` - Exclude files with type=partial_conversion in meta information
- `--has-document-annotation` - Only include files with document level annotation
- `--no-document-annotation` - Only include files without document level annotation
- `--pretty` - Output pretty-printed JSON

### Examples

1. Convert all UMR files to JSON:
   ```bash
   python parse_umr_to_json.py
   ```

2. Convert only English UMR files:
   ```bash
   python parse_umr_to_json.py --language english
   ```

3. Convert only files with document level annotation:
   ```bash
   python parse_umr_to_json.py --has-document-annotation
   ```

4. Convert only Czech files without partial conversion:
   ```bash
   python parse_umr_to_json.py --language czech --no-partial-conversion
   ```

### Output Format

The script outputs a JSON file containing an array of UMR documents. Each document has the following structure:

```json
{
  "filename": "english_umr-0001.umr",
  "language": "english",
  "blocks": [
    {
      "meta_info": {
        "sent_id": "u_tree-cs-s1-root",
        "snt1": ""
      },
      "sentence_info": {
        "Index": "1 2 3 4 5 6 7 8 9 10",
        "Words": "200 dead , 1,500 feared missing in Philippines landslide ."
      },
      "sentence_annotation": "(s1p / publication-91 :ARG1 (s1l / landslide-01...))",
      "alignment": "s1p: 0-0\ns1l: 9-9...",
      "document_annotation": "(s1s0 / sentence :temporal ((document-creation-time :before s1l)...))",
      "has_document_annotation": true
    },
    {
      // Additional blocks for other sentences in the file
    }
  ]
}
```

## UMR 3.0 Data Format Description

(See also [here](https://ufal.mff.cuni.cz/umr-parsing/umr-file-format).)

Each UMR file corresponds to one **document** (document-level annotation thus does not refer to other files).

The document is organized in **segments**, each corresponding to a single sentence.
Each sentence segment starts with a line of 80 hash signs and ends with two empty lines.

### Sentence Structure

Within each sentence segment, there are **four parts**.
Each of them starts with a comment line (a line whose first character is a hash sign)
and ends with one empty line (except the last part of the sentence, which ends with two empty lines).
The four parts are as follows:

---

### 1. Sentence Information

#### Meta Information

- Entries are separated by two colons (`::`).
- Example entries:
  - `type = partial_conversion`: Indicates that the UMR annotation for this sentence was converted from AMR or from PDT.
  - `sent_id = u_tree-cs-s1-root`: Maps to the original sentence ID from the source workset.

#### Tokens, Morphemes, Translation

This section may include the following fields:

- **Index**: Token indices (to be used in the alignment block below)
- **Words**: Tokens of the sentence (separated by one or more spaces, same number of elements as in Index)
- **Word Gloss (en)**: English translation of the individual words
- **Word Gloss (es)**: Spanish translation of the individual words
- **Morphemes**: Morphological breakdown of words
- **Morpheme Gloss (en)**: English glosses of morphemes
- **Morpheme Gloss (es)**: Spanish glosses of morphemes
- **Morpheme Category**: Categories or grammatical roles of morphemes
- **Part of Speech**: Part-of-speech tags
- **Sentence**: Original untokenized sentence
- **Translation (en)**: English translation of the sentence
- **Translation (es)**: Spanish translation of the sentence

---

### 2. Sentence-Level UMR Annotation

- UMR structure is represented in **Penman notation**.

---

### 3. Alignment Information

- Alignments between UMR concepts and token indices.

---

### 4. Document-Level Annotation

- UMR structure is represented by temporal/model/coreference relation triples.


---

## Language Coverage

This dataset includes annotated data from the following languages (ISO 639-3 codes):

- Arapaho (arp)
- Chinese (zho)
- Czech (ces)
- English (eng)
- Italian (ita)
- Kukama (cod)
- Latin (lat)
- Navajo (nav)
- Portuguese (por)
- Sanapaná (spn)

### Changelog

#### [UMR 3.0 Release](http://hdl.handle.net/11234/1-6224)

- Added PUD dataset for Portuguese
- More English and Chinese files
- Format fixes in previously released data (now also in Kukama and Sanapaná)

#### [UMR 2.2 Release](http://hdl.handle.net/11234/1-6132) (2026-04-01)

- Added parallel PUD datasets of Czech, English, and Italian
- Numerous format fixes in English, Chinese, Arapaho, and Navajo
- New annotated data in Chinese
- Specific only to this release (not preserved in the subsequent one):
  - Training-test splits as used in UMR Parsing Shared Task at DMR 2026
  - System outputs on test data from the shared task

#### [UMR 2.1 Release](http://hdl.handle.net/11234/1-5951) (2025-06-30)

- Improved annotation of Czech and Latin

#### [UMR 2.0 Release](http://hdl.handle.net/11234/1-5902) (2025-05-17)

- Added Czech (converted from Prague Dependency Treebank) and Latin (manual annotation)
- More English data (partial annotation, automatically converted from AMR)

#### [UMR 1.0 Release](http://hdl.handle.net/11234/1-5198) (2023-07-31)

- Initial annotation of 6 languages: English, Chinese, Arapaho, Kukama, Navajo, Sanapaná

---

### Notes

For detailed mapping between the current file names and their original workset names, refer to the provided **umr_file_name_mapping.txt**.

The file **validation.log** contains output of the [UMR validation script](https://github.com/ufal/umrtools),
invoked as follows:

```bash
for i in */umr_data/*.umr ; do \
    echo $i ; \
    /net/work/people/zeman/umr/umrtools/validate.py \
        --no-check-ilg --allow-forward-references --allow-cycles --allow-duplicate-roles \
        --optional-aspect-modstr --no-check-wiki --optional-alignments --no-warn-unaligned-token \
        --allow-coref-entity-event-mismatch \
        $i ; \
done 2>&1 | tee validation.log
```

## Statistics Tables Description

Run `statistics.py` to generate the `umr_statistics.txt` file, which contains summary tables.

### Notes:
- The following descriptions explain the metrics used in the three types of tables.
- **Partial-conversion data** refers to data that have been partially converted from AMR or PDT.
- **Non-partial-conversion data** includes data that were manually annotated.


### Stats for ALL

| Metric    | Count                            |
|-----------|----------------------------------|
| Documents | Total documents of this language |

---

### Stats for PARTIAL-CONVERSION

| Metric                     | Count                                                             |
|----------------------------|-------------------------------------------------------------------|
| Documents                  | Documents that contain at least one partial annotation            |
| Sentences (Blocks)         | Sentences that have partially converted annotations                |
| Words                      | Total words of sentences that have partially converted annotations |
| Sentence-level Graphs      | Partially converted sentence level annotations                    |
| Doc-level Graphs           | Partially converted document level annotations                    |
| Relations (Sentence-level) | Total relations in partially converted sentence level annotations  |
| Concepts (Sentence-level)  | Total concepts in partially converted annotations                  |
| Relations (Document-level) | Total relations in partially converted document level annotations  |

---

### Stats for NON-PARTIAL-CONVERSION Blocks

| Metric                     | Count                                                                 |
|----------------------------|------------------------------------------------------------------------|
| Documents                  | Documents that contain at least one non-partial annotation            |
| Sentences (Blocks)         | Sentences that have non-partially converted annotations                |
| Words                      | Total words of sentences that have non-partially converted annotations |
| Sentence-level Graphs      | Manually annotated sentence level graphs                    |
| Doc-level Graphs           | Manually annotated document level graphs                    |
| Relations (Sentence-level) | Total relations in manually annotated sentence level annotations  |
| Concepts (Sentence-level)  | Total concepts in manually annotated annotations                  |
| Relations (Document-level) | Total relations in manually annotated document level annotations  |
