# Thesis Paper

This repository branch contains the full LaTeX source of an undergraduate thesis at Lanzhou University, titled:

**"Cathepsin Family: Mechanisms and Impact on Aging of Physiological Barriers"**  
（组织蛋白酶家族对于体内屏障衰老的作用与机制）

The thesis explores how members of the **cathepsin family** influence **tissue barrier aging**, using _Caenorhabditis elegans_ as a model organism. By employing **RNA interference (RNAi)** and phenotypic assays, the study reveals novel insights into the regulation of intercellular junction integrity during aging. It builds upon earlier findings and extends the understanding of **cathepsin-mediated epithelial deterioration**, offering fresh perspectives and molecular targets for aging-related interventions.

---

## 📁 Directory Structure

```

.
├── bib/               # Bibliographic database and citation style files
├── chapters/          # Thesis chapters (main content)
├── img/               # Figures and scanned signature images
├── output/            # Compiled output files (e.g., PDF)
├── temp/, log/        # Temporary files and logs (Git-ignored)
├── paper.tex          # Main LaTeX entry file
├── LZUThesis.cls      # Lanzhou University thesis class file

```

---

## 🔧 Compilation

To compile the thesis, use the following script:

```bash
#!/bin/bash

TEX_FILE="paper.tex"
OUTPUT_DIR="./output"
TEMP_DIR="./temp"
LOG_DIR="./log"

mkdir -p "$OUTPUT_DIR" "$TEMP_DIR" "$LOG_DIR"
rm -f "$TEMP_DIR"/*

echo "Compiling $TEX_FILE with xelatex..."
xelatex -interaction=nonstopmode -output-directory="$TEMP_DIR" "$TEX_FILE" > "$LOG_DIR/latex.log" 2>&1

echo "Processing bibliography..."
bibtex "$TEMP_DIR/$(basename "$TEX_FILE" .tex)" > "$LOG_DIR/bibtex.log" 2>&1

echo "Running xelatex passes..."
xelatex -interaction=nonstopmode -output-directory="$TEMP_DIR" "$TEX_FILE" > "$LOG_DIR/latex2.log" 2>&1
xelatex -interaction=nonstopmode -output-directory="$TEMP_DIR" "$TEX_FILE" > "$LOG_DIR/latex3.log" 2>&1

mv "$TEMP_DIR/$(basename "$TEX_FILE" .tex).pdf" "$OUTPUT_DIR/"
echo "Compilation complete. PDF saved to $OUTPUT_DIR."
```

Alternatively, you can compile using **VSCode + LaTeX Workshop** with **XeLaTeX** selected.

> Make sure to use XeLaTeX to support Chinese fonts and Unicode.

---

## ⚠️ Notes

- Signature images (`my_signature.png`, `teacher_signature.png`) are **not included** and should be added manually under the `img/` folder.
- This thesis uses a rich set of packages including `tcolorbox`, `tikz`, and `forest` to present data, diagrams, and custom-styled elements.

---

## 📄 License

This work is licensed under the **Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License**.
View the license here:
👉 [http://creativecommons.org/licenses/by-nc-nd/4.0/](http://creativecommons.org/licenses/by-nc-nd/4.0/)

> You may share the work for non-commercial purposes with attribution.
> Derivatives or modified versions are **not allowed**.

---

## ✍️ Author

**Zhang Weihua（张蔚华）**
Undergraduate Student, Cuiying Honors College, Lanzhou University
Graduation Year: 2025

> _“愿你带着春天的印记远航，在科研和生活中播撒梦想的种子。”_
