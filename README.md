<p style="border:1px; border-style:solid; border-color:black; padding: 1em;">
CS-UH 3260 Software Analytics<br/>
Replication Study Guidelines<br/>
Dr. Sarah Nadi, NYUAD
</p>

# Replication 5 -- CS-UH-3260 Software Analytics


## Overview

This repo contains the scripts and data used for the `Replication 5` assignment, focusing on the paper *Beyond Bug Fixes: An Empirical Investigation of Post-Merge Code Quality Issues in Agent-Generated Pull Requests*. The scope of our replication includes...


### 1. Project Title and Overview

- **Paper Title**: Beyond Bug Fixes: An Empirical Investigation of Post-Merge Code Quality Issues in Agent-Generated Pull Requests
- **Authors**: Shamse Tasnim Cynthia, Al Muttakin, Banani Roy
- **Replication Team**: Matthias Kebede and Muhammad Arhum
- **Course**: CS-UH 3260 Software Analytics, NYUAD
- **Brief Description**: 
  - *Beyond Bug Fixes* looks at a subset of the **AIDev** dataset in order to assess the quality of Agentic PRs, specifically looking at bugfixes. They specifically look at code quality issues introduced by agents through SonarQube analysis of the *base* and *merged* commits. This reveals patterns in the distribution of issues across severity, type, and agent.
  - Our replication aims to validate the results of the original paper. We use the included Jupyter Notebooks to run the SonarQube analysis and calculate the final results, then compare them to the claimed findings.


### 2. Repository Structure

Document your repository structure clearly. Organize your repository using the following standard structure:

```
README                              # Documentation
datasets/                           # The original datasets taken from the package
  All_PR_Issues_Details_with_LOC.csv    # An extended version of including added/deleted lines (~churn)
  All_PR_Sonar_Results.json             # Contains all of the info from analyzing the PRs w/ SonarQube
  python_fix_prs.csv                    # This is the filtered subset of PRs from the AIDev set
  Security_Hotspot_Details.json         # Shows the distribution of 'Security Hotspot' issues found in SonarQube
replication_scripts/
  SonarAnalysis.ipynb                   # Runs SonarQube analysis and prepares necessary CSV/JSON files
  result-analysis.ipynb                 # Performs the analysis and statistical tests, outputs: CSVs, PNG tables, LaTeX tables
outputs/
  Agent_Statistics_Summary.csv          # Shows how many PRs and Issues per Agent
  Agent_Statistics_Summary.tex
  issue_density.png                     # Box-and-Whisker plot w/ outliers removed
  (additional outputs in branch)
logs/
  process.log                           # Logs generated during SonarQube analysis
notes/
  notes.md                              # General notes
  Kebede_Task1.md                       # Task 1 analysis (Matthias branch)
```

For reference, none of the dataset files appear to come directly from the AIDev dataset, although it obviously draws from it as a base to populate its own subset.


### 3. Setup Instructions

- **Prerequisites**:
  - Python 3.8+ and Git
  - SonarQube Scanner (and SonarQube Cloud if using Google Colab - **Note: has LOC limits depending on plan**)
  - Jupyter Notebook or JupyterLab

- **Installation Steps (Local)**:
  - Clone the replication package using `git clone git@github.com:cynthia247/MSR-Mining-2026.git`
  - Create a `.env` file to pass sensitive values (i.e. GitHub Token, Sonar Token)
  - Create a virtual environment and install required libraries:
    - You may also need to install `scikit_posthocs`/`pyarrow` if you encounter a ModuleNotFoundError
  ```bash
  python -m venv .venv
  source .venv/bin/activate              # `.venv/scripts/activate` on Windows)
  pip install pandas numpy matplotlib seaborn requests python-dotenv       # as per the package's README
  ```

- **Running Instructions**:
  - Ensure that SonarQube is running (e.g. `docker run -d --name sonarqube -p 9000:9000 sonarqube:community`) and SonarScanner responds (`sonar-scanner -v`)
  - Open the `SonarAnalysis.ipynb` file and edit the constants to reflect your environment (e.g. `REPO_DIR=...`)
  - Simply run the cells in each notebook in order (the file names can be very inconsistent, so be very careful about checking them)
    - You can try running the Result Analysis using the original dataset files first, otherwise start with the SonarQube Analysis
  - The Result Analysis should produce any CSVs and tables needed (in PNG and/or LaTeX format)

- **Alternative Setup for Google Colab**:
  - Open a notebook and set up the repository:
  ```bash
  !git clone https://github.com/cynthia247/MSR-Mining-2026.git
  %cd MSR-Mining-2026
  !pip install pandas numpy matplotlib seaborn requests python-dotenv
  ```
  - Install SonarQube in the Colab environment (cell provided)
  - Signup/Login to SonarQube Cloud and generate a token
  - Add GitHub/SonarQube tokens to Google Colab keys & edit constants as needed (i.e. `REPO_DIR`, `SONAR_URL`, `PROJECT_KEY`)

- **Running Instructions (Google Colab)**
  - Run the included scripts:
    - We use the `-i` flag in order to pass variables (e.g. those that cause a NameError otherwise)
    - You can try running the Result Analysis script first to make sure everything is in order
    - Alternatively, you can open the `.ipynb` files directly in Colab or otherwise transfer the individual cells over --> run step by step
  ```bash
  # Sonar analysis
  %run /content/MSR-Mining-2026/Scripts/SonarAnalysis.ipynb
  ```
  ```bash
  # Result analysis
  issue_types = ['BUG', 'CODE_SMELL', 'SECURITY_HOTSPOT']
  rule_col = 'Rule'
  %run -i /content/MSR-Mining-2026/Scripts/result-analysis.ipynb
  ```
  - You may need to rename/move the dataset files to fix any FileNotFound discrepancies (we include a cell to handle all the necessary changes)
  - Save any files or console output needed


### 4. GenAI Usage

  - **Gemini** - Used to help with Google Colab syntax & file handling + set up SonarQube
  - **Copilot** - Used to help w/ LaTeX syntax and resolving inconsistencies in the Jupyter Notebooks










## Grading Criteria for README

Your README will be evaluated based on the following aspects (Total: 40 points):

### 1. Completeness (10 points)
- [ ] All required sections are present
- [ ] Each section contains sufficient detail
- [ ] Repository structure is fully documented
- [ ] All files and folders are explained
- [ ] GenAI usage is documented (if any AI tools were used)

### 2. Clarity and Organization (5 points)
- [ ] Information is well-organized and easy to follow
- [ ] Instructions are clear and unambiguous
- [ ] Professional writing and formatting
- [ ] Proper use of markdown formatting (headers, code blocks, lists)

### 3. Setup and Reproducibility (10 points)
- [ ] Setup instructions are complete and accurate, i.e., we were able to rerun the scripts following your instructions and obtain the results you reported


## Best Practices

1. **Be Specific**: Include exact versions, paths, and commands rather than vague descriptions
2. **Keep It Updated**: Ensure the README reflects the current state of your repository
3. **Test Your Instructions**: Have someone else (or yourself in a fresh environment) follow the setup instructions
4. **Document AI Usage**: If you used any GenAI tools, be transparent about how they were used (e.g., understanding scripts, exploring datasets, understanding data fields)


## Acknowledgement

This guideline was developed with the assistance of [Cursor](https://www.cursor.com/), an AI-powered code editor. This tool was used to:

- Draft and refine this documentation iteratively
