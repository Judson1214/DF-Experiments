# Experiment 08: Steganalysis & LSB Statistical Anomaly Detection Using StegExpose

[![Forensics](https://img.shields.io/badge/Forensics-Steganography%20Detection-blue.svg)](#)
[![Tools](https://img.shields.io/badge/Tools-StegExpose%20CLI-yellow.svg)](#)
[![Status](https://img.shields.io/badge/Status-Completed-success.svg)](#)

---

## 📌 Navigation
[⬅️ Experiment 07: AFLogical Android Extraction](../Experiment-7/README.md) | [🏠 Master Syllabus](../README.md) | [Experiment 09: Process Explorer ➡️](../Experiment-9/README.md)

---

## 🎯 1. Aim
To conduct a comprehensive steganalysis lifecycle on digital image evidence using the **StegExpose** command-line utility; to evaluate Least Significant Bit (LSB) statistical properties and detection algorithms across a target evidence directory; to compute quantitative suspicion scores based on configurable thresholds; and to automatically compile, format, and export the analytical findings into a structured CSV report for forensic documentation.

---

## 🛠️ 2. Software & Tools Required
| Tool / Utility | Version / Type | Purpose | Platform |
| :--- | :--- | :--- | :--- |
| **StegExpose** | Java CLI (`StegExpose.jar`) | Batch LSB steganalysis detection engine | Cross-platform (JRE) |
| **Java Runtime Environment (JRE)** | Java 8+ / OpenJDK 17+ | Runtime execution engine for `.jar` archive | Windows / Linux |
| **Test Image Dataset** | PNG, BMP, JPG images | Carrier images (clean and suspected steganographic payloads) | File System |

---

## 📖 3. Theoretical Background & Key Concepts

### 3.1 LSB Steganography
Least Significant Bit (LSB) steganography embeds secret data into the lowest bit of pixel color bytes (e.g., Red, Green, Blue channels of 24-bit bitmap/PNG images). Modifying the least significant bit alters the color intensity by only $\pm 1/255$th of its value—an alteration invisible to the human visual system (HVS).

### 3.2 StegExpose Detection Algorithms
StegExpose combines four complementary LSB statistical detection algorithms to detect anomalies in pixel distributions:
1. **Primary Sets (Chi-Square Analysis):** Measures differences between pairs of values (PoVs).
2. **Sample Pair Analysis (SPA):** Detects modifications in adjacent sample pairs caused by bit substitution.
3. **RS Analysis (Regular / Singular groups):** Analyzes changes in noise patterns when an inversion mask is applied.
4. **Weighted Stego (WS) Analysis:** Weighs spatial dependencies and adjacent pixel correlations.

### 3.3 Quantitative Suspicion Thresholds
- **Score < 0.20:** Clean image (no statistically significant anomaly).
- **0.20 $\le$ Score $\le$ 0.30:** Indeterminate / possible steganographic presence.
- **Score > 0.30:** High suspicion / steganographic payload detected.

---

## 🔬 4. Step-by-Step Procedure

### Step 1: Java Runtime Environment Verification
1. Open the terminal or Command Prompt.
2. Verify that Java is installed and accessible in the system path:
```bash
java -version
```

![Fig 8.1: JDK Verification](images/image1.png)
*Figure 8.1: Verifying Java Runtime Environment installation.*

---

### Step 2: Preparing Evidence Directory
1. Assemble the target image directory containing suspected carrier media (`suspect_image.png`, `carrier.bmp`, `clean_sample.png`).
2. Verify directory contents using `dir` (Windows) or `ls -l` (Linux).

![Fig 8.2: Environment Setup](images/image2.png)
*Figure 8.2: Initializing StegExpose CLI within evidence working directory.*

![Fig 8.3: Inspecting Target Images](images/image3.png)
*Figure 8.3: Directory listing of target evidence images queued for steganalysis.*

---

### Step 3: Single-Image Steganalysis Execution
1. Run StegExpose against an individual suspicious image:
```bash
java -jar StegExpose.jar suspect_image.png
```
2. Interpret the console output score:
```text
Analyzing suspect_image.png...
Result: 0.4
Steganography likely present
```
*Assessment:* A score of `0.4` exceeds the `0.3` threshold, confirming payload presence.

---

### Step 4: Batch Analysis Across Target Evidence Directory
1. Execute StegExpose in batch mode across the entire evidence folder, configuring speed settings, threshold filters, and CSV report export:
```bash
java -jar StegExpose.jar "C:\Evidence\Images" default.speed 0.2 results.csv
```

![Fig 8.4: Batch Scanning in Progress](images/image4.png)
*Figure 8.4: StegExpose executing batch LSB analysis across evidence directory.*

![Fig 8.5: Processing Anomaly Metrics](images/image5.png)
*Figure 8.5: Real-time calculation of statistical scores and threshold checks.*

---

### Step 5: Reviewing the Structured CSV Report
1. Open `results.csv` using spreadsheet software or a text viewer.
2. Review the compiled findings:
   - **Image Filename**
   - **Calculated Suspicion Score**
   - **Threshold Determination (Clean / Suspicious)**
   - **Estimated Secret Message Size (bytes)**

![Fig 8.6: Final Results CSV Report](images/image6.png)
*Figure 8.6: Exported results.csv spreadsheet detailing quantitative steganalysis findings.*

---

## 📊 5. Observations & Forensic Findings
| Image Artifact | Calculated Score | Threshold Category | Determination |
| :--- | :---: | :---: | :--- |
| `suspect_image.png` | **0.40** | Score > 0.30 | **Steganography Likely Present** (LSB modification detected) |
| `sample_clean.bmp` | **0.04** | Score < 0.20 | **Clean** (No statistical anomaly) |
| `benchmark_test.png`| **0.25** | 0.20 - 0.30 | **Indeterminate** (Manual RS analysis recommended) |

---

## 🏆 6. Result
The steganography detection experiment was successfully executed using **StegExpose**. The utility scanned the evidence directory via the command line, analyzed combinations of LSB metrics (Sample Pair Analysis, RS, and Chi-Square), and generated a structured CSV report detailing the cleanliness and suspicion levels of each digital image artifact.
