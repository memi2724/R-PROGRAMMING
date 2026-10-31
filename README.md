[readme_md.md](https://github.com/user-attachments/files/34209213/readme_md.md)
# Statistics with R Programming Lab (ITA04)

This repository contains the R scripts, implementations, and execution outputs for **Experiments 1 to 21**.

---

## Repository Structure

* `scripts/` – Individual R scripts for each experiment (`01_vectors.R` through `21_logistic_iris.R`).
* `outputs/` – Console output text files corresponding to each script.

To execute and regenerate all outputs automatically:
```bash
Rscript run_all.R
```
*(Run this command from the repository root directory)*

---

## List of Experiments

1. **Experiment 1:** Create numeric, character, and logical vectors
2. **Experiment 2:** Create labeled matrices ($5\times4$, $3\times3$, $2\times2$)
3. **Experiment 3:** Create and display a 3D array
4. **Experiment 4:** Arrays with dimension names; print specific elements
5. **Experiment 5:** Create and manipulate factor variables
6. **Experiment 6:** List containing vectors, matrices, and functions
7. **Experiment 7:** Factors of a number, random integers, and FizzBuzz
8. **Experiment 8:** Normal distribution random numbers; count occurrences
9. **Experiment 9:** Empty plot with specified axis limits *(produces plot)*
10. **Experiment 10:** Data frame `exam_data`: extract, add, sort, save
11. **Experiment 11:** Read a `.csv` file and display contents
12. **Experiment 12:** Reshape `airquality`: monthly averages (`melt`/`cast`)
13. **Experiment 13:** Combine arrays row-wise
14. **Experiment 14:** `ChickWeight`: sorting, melting, casting by Diet
15. **Experiment 15:** EDA on the `iris` dataset
16. **Experiment 16:** Explore the `USArrests` dataset *(produces plots)*
17. **Experiment 17:** Explore the `Titanic` dataset *(produces plots)*
18. **Experiment 18:** Graphs: boxplot, histogram, bar, line, scatter *(produces plots)*
19. **Experiment 19:** Simple linear regression (`Sales ~ Spend`)
20. **Experiment 20:** Multiple regression on `ChickWeight`
21. **Experiment 21:** Logistic regression on `iris` with 80/20 train-test split

> **Note on Graphical Outputs:** Experiments 9, 16, 17, and 18 generate visual plots. Open and run these scripts inside RStudio to view the graphs directly.

---

## Requirements & Setup

* R (version 4.0 or higher recommended)
* Required packages:
  ```r
  install.packages("reshape2")
  ```

---

## Running an Individual Script

To run any individual experiment from the command line:
```bash
Rscript scripts/01_vectors.R
```
