# Prokaryotic-Genome-Annotation-Pipeline-for-Bacillus-Subtilis-ERR14842915

## **Overview**

In this pipeline, I created a non-reproducible but complete genome assembly and annotation of Bacillus Subtilis (ENA ID: ERR14842915). During which I measured its quality scores using QUAST, assembled reads using SPAdes, performed scaffolding with Unicycler, and annotated genes to determine their functional relevance  using PROKKA. This pipeline is currently in use at the Bruhaspathi Institute of Bioscience as they adopted this pipeline

## **Methodology**

### **1. Data Acquisition**
The paired-end Illumina reads for *Bacillus subtilis* were downloaded manually from the [ENA database](https://www.ebi.ac.uk/ena/browser/view/ERR14842915).  
These files were placed into the working directory using **WinSCP**, serving as the input for subsequent steps.

### **2. Quality Control**
The raw reads were first assessed using **FastQC** to evaluate parameters such as base quality, GC distribution, and adapter contamination.  
This step helped in understanding overall read quality before trimming.

### **3. Read Trimming**
Low-quality regions and adapter sequences were removed using **Trimmomatic**.  
This ensured that only high-quality paired reads were retained for downstream analysis, improving assembly accuracy.

### **4. Post-trimming Quality Check**
The cleaned reads were again analyzed with **FastQC** to confirm quality improvements and verify that trimming did not affect sequence coverage or content.

### **5. Genome Assembly**
Initial attempts were made using **SPAdes**, but due to memory constraints, the assembly was finalized with **Unicycler**, which successfully generated **71 contigs**.  
Unicycler was chosen for its hybrid assembly optimization and efficient handling of paired-end reads.

### **6. Gene Annotation**
Structural and functional annotation was performed using **Prokka**, which identifies coding sequences (CDS), rRNAs, and tRNAs.  
Species-specific parameters were used to tailor the annotation for *Bacillus subtilis*, resulting in a detailed and biologically meaningful annotation output.

### **7. Quality Assessment**
The assembled and annotated genome was evaluated with **QUAST** to measure quality metrics such as N50, number of contigs, and completeness.  
This provided confidence that the resulting genome assembly and annotation were of high integrity.

---

## **Output Summary**
- **Total Contigs:** 71  
- **Assembly Quality:** Evaluated using QUAST with gene completeness thresholds  
- **Annotation:** Functional genes, rRNA, and tRNA predictions from Prokka  
- **Final Deliverables:**  
  - `assembly.fasta` – final assembled genome  
  - `ERR14842915.gff` – annotated gene features  
  - `quast_results/` – quality assessment metrics  
  - `prokka_results/` – annotated genome files (FAA, FNA, GBK, TXT)

---

## **Environment Requirements**

### **Software Stack**
- **Operating System:** Linux / macOS (Apple Silicon compatible)  
- **Package Manager:** Conda / Miniconda  
- **Programming Language:** Python ≥ 3.8  
- **Core Tools:**
  - FastQC  
  - Trimmomatic  
  - Unicycler  
  - Prokka  
  - QUAST  
  - Samtools  
  - Pilon  
  - Java JDK  

The pipeline was designed and tested within isolated conda environments for reproducibility.

---

## **Reproducing the Workflow**

To reproduce or run this pipeline locally:

1. **Clone this repository**
   ```bash
   git clone https://github.com/ParthivRajesh/BacillusSubtilis_GenomeAnnotation.git
   cd BacillusSubtilis_GenomeAnnotation

