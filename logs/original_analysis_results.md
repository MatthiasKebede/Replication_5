This is the output from running the Result Analysis scripts using the existing data (before running the SonarQube):

```
 Issue distribution across agents: 
Agent
OpenAI_Codex    949
Copilot         106
Devin           100
Cursor           40
Claude_Code      15
Name: count, dtype: int64
==================================================================================================================================
COMPREHENSIVE STATISTICAL ANALYSIS OF ISSUES PER PR BY AGENT
==================================================================================================================================

       Agent  Total PRs  PRs with Issues  PRs without Issues  % PRs with Issues  Total Issues  Mean  Median  Std Dev  Min  Max  Q1  Q3  IQR  Outliers
 Claude_Code         15                8                   7              53.33            69  4.60     1.0     9.56    0   35 0.0 2.5  2.5         3
     Copilot        106               22                  84              20.75           235  2.22     0.0    10.14    0   94 0.0 0.0  0.0        22
      Cursor         40                9                  31              22.50           331  8.28     0.0    38.19    0  233 0.0 0.0  0.0         9
       Devin        100               26                  74              26.00            99  0.99     0.0     2.77    0   22 0.0 1.0  1.0        12
OpenAI_Codex        949              125                 824              13.17           456  0.48     0.0     2.58    0   30 0.0 0.0  0.0       125

==================================================================================================================================

✓ Table saved to: Agent_Statistics_Summary.csv

==================================================================================================================================
LATEX TABLE FORMAT (Copy-paste into your research paper)
==================================================================================================================================

\begin{table}[h]
\centering
\caption{Statistical Analysis of Issues per PR by AI Coding Agent}
\label{tab:agent_statistics}
\resizebox{\textwidth}{!}{%
\begin{tabular}{lrrrrrrrrrrrrrr}
\hline
\textbf{Agent} & \textbf{Total PRs} & \textbf{PRs w/ Issues} & \textbf{PRs w/o Issues} & \textbf{\% w/ Issues} & \textbf{Total Issues} & \textbf{Mean} & \textbf{Median} & \textbf{Std Dev} & \textbf{Min} & \textbf{Max} & \textbf{Q1} & \textbf{Q3} & \textbf{IQR} & \textbf{Outliers} \\
\hline
Claude_Code & 15 & 8 & 7 & 53.33 & 69 & 4.60 & 1.00 & 9.56 & 0 & 35 & 0.00 & 2.50 & 2.50 & 3 \\
Copilot & 106 & 22 & 84 & 20.75 & 235 & 2.22 & 0.00 & 10.14 & 0 & 94 & 0.00 & 0.00 & 0.00 & 22 \\
Cursor & 40 & 9 & 31 & 22.50 & 331 & 8.28 & 0.00 & 38.19 & 0 & 233 & 0.00 & 0.00 & 0.00 & 9 \\
Devin & 100 & 26 & 74 & 26.00 & 99 & 0.99 & 0.00 & 2.77 & 0 & 22 & 0.00 & 1.00 & 1.00 & 12 \\
OpenAI_Codex & 949 & 125 & 824 & 13.17 & 456 & 0.48 & 0.00 & 2.58 & 0 & 30 & 0.00 & 0.00 & 0.00 & 125 \\
\hline
\end{tabular}%
}
\end{table}

✓ LaTeX table saved to: Agent_Statistics_Summary.tex

==================================================================================================================================
====================================================================================================
ISSUE DENSITY ANALYSIS (SIZE-NORMALIZED)
====================================================================================================

Checking for LOC/Size metrics in the dataset...
Available columns: ['Owner/Repo', 'PR Number', 'agent', 'html_url', 'Issue Type', 'Severity', 'Message', 'File Name', 'StartLine', 'EndLine', 'Rule', 'additions', 'deletions', 'changed_files', 'changed_loc']

Size-related columns found: ['StartLine', 'EndLine', 'additions', 'deletions', 'changed_files', 'changed_loc']

✓ Using 'StartLine' as size metric
✓ Using 'changed_loc' as size metric


✓ Calculated issue density (issues per KLOC)
  Total PRs analyzed: 189

====================================================================================================
1. DESCRIPTIVE STATISTICS - ISSUE DENSITY BY AGENT
====================================================================================================

       Agent   N        Mean     Median     Std Dev      Min        Q1         Q3          Max
 Claude_Code   8 1523.344384  15.148883 4100.523649 0.555710  2.050654 176.542208 11666.666667
     Copilot  21 1409.645163  41.666667 5257.411110 1.694915 19.607843 105.263158 24000.000000
      Cursor   9  937.558173 200.000000 2087.153168 0.362188  9.009009 571.428571  6454.545455
       Devin  26  238.371933  25.320513  714.863077 4.132231 10.686063 104.166667  3500.000000
OpenAI_Codex 125  348.918774  39.215686 1236.497556 1.102536 15.384615  90.909091  8500.000000

====================================================================================================
2. KRUSKAL-WALLIS TEST (Non-parametric ANOVA)
====================================================================================================

H-statistic: 3.0450
p-value: 5.5032e-01

✗ No significant difference detected (p ≥ 0.05)
  → Post-hoc tests not recommended

====================================================================================================
3. POST-HOC DUNN TEST (Pairwise Comparisons)
====================================================================================================

Skipped (Kruskal-Wallis was not significant)

====================================================================================================
4. CLIFF'S DELTA EFFECT SIZE (Pairwise)
====================================================================================================

Interpretation: |δ| < 0.147: negligible, < 0.33: small, < 0.474: medium, ≥ 0.474: large

                 Comparison  Cliff's Delta  Magnitude  n1  n2
     Claude_Code vs Copilot         -0.214      small   8  21
      Claude_Code vs Cursor         -0.278      small   8   9
       Claude_Code vs Devin         -0.202      small   8  26
Claude_Code vs OpenAI_Codex         -0.210      small   8 125
          Copilot vs Cursor         -0.206      small  21   9
           Copilot vs Devin          0.117 negligible  21  26
    Copilot vs OpenAI_Codex          0.014 negligible  21 125
            Cursor vs Devin          0.274      small   9  26
     Cursor vs OpenAI_Codex          0.236      small   9 125
      Devin vs OpenAI_Codex         -0.103 negligible  26 125

====================================================================================================
5. VISUALIZATION
====================================================================================================

Original data points: 189
Data points after removing outliers: 161
Outliers removed: 28

✓ Box plot generated (outliers removed, quartile analysis)

====================================================================================================
HIERARCHICAL TABLE: ISSUE TYPES (with Severity) × AGENTS
====================================================================================================

                Issue Type Severity  Claude_Code  Copilot  Cursor  Devin  OpenAI_Codex
                       BUG  BLOCKER           16        4       0      1            20
                              MAJOR            1        0       0      2             4
             **BUG Total**                    17        4       0      3            24
                CODE_SMELL  BLOCKER            0        0       2      0             1
                           CRITICAL           28      166     129     45           162
                               INFO            2       16       8      3            66
                              MAJOR           12       31     124     10            98
                              MINOR            3        7      66     21            59
      **CODE_SMELL Total**                    45      220     329     79           386
          SECURITY_HOTSPOT     HIGH            1        0       1      0             5
                                LOW            6       10       0     17            26
                             MEDIUM            0        1       1      0            15
**SECURITY_HOTSPOT Total**                     7       11       2     17            46
           **GRAND TOTAL**                    69      235     331     99           456

✓ Table saved: Hierarchical_Issue_Type_Severity_Agent_Table.csv

====================================================================================================
LATEX TABLE FORMAT
====================================================================================================

\begin{table}[htbp]
\centering
\caption{Hierarchical Distribution of Issues by Type, Severity, and Agent}
\label{tab:hierarchical_issue_distribution}
\resizebox{\textwidth}{!}{%
\begin{tabular}{llrrrrr}
\toprule
\textbf{Issue Type} & \textbf{Severity} & \textbf{Claude_Code} & \textbf{Copilot} & \textbf{Cursor} & \textbf{Devin} & \textbf{OpenAI_Codex} \\
\midrule
BUG & BLOCKER & 16 & 4 & 0 & 1 & 20 \\
 & MAJOR & 1 & 0 & 0 & 2 & 4 \\
\textbf{BUG Total} &  & \textbf{17} & \textbf{4} & \textbf{0} & \textbf{3} & \textbf{24} \\
\midrule
CODE_SMELL & BLOCKER & 0 & 0 & 2 & 0 & 1 \\
 & CRITICAL & 28 & 166 & 129 & 45 & 162 \\
 & INFO & 2 & 16 & 8 & 3 & 66 \\
 & MAJOR & 12 & 31 & 124 & 10 & 98 \\
 & MINOR & 3 & 7 & 66 & 21 & 59 \\
\textbf{CODE_SMELL Total} &  & \textbf{45} & \textbf{220} & \textbf{329} & \textbf{79} & \textbf{386} \\
\midrule
SECURITY_HOTSPOT & HIGH & 1 & 0 & 1 & 0 & 5 \\
 & LOW & 6 & 10 & 0 & 17 & 26 \\
 & MEDIUM & 0 & 1 & 1 & 0 & 15 \\
\textbf{SECURITY_HOTSPOT Total} &  & \textbf{7} & \textbf{11} & \textbf{2} & \textbf{17} & \textbf{46} \\
\midrule
\midrule
\textbf{GRAND TOTAL} &  & \textbf{69} & \textbf{235} & \textbf{331} & \textbf{99} & \textbf{456} \\
\bottomrule
\end{tabular}%
}
\end{table}

✓ LaTeX table saved: Hierarchical_Issue_Type_Severity_Agent_Table.tex

====================================================================================================
TABLE SUMMARY
====================================================================================================
Total rows: 14
Total agents: 5
CSV and LaTeX files ready for use in your paper!
Note: LaTeX table requires \usepackage{booktabs} in your document preamble

====================================================================================================
GENERATING LATEX TABLE: TOP 5 MOST VIOLATED RULES PER ISSUE TYPE
====================================================================================================


BUG:
--------------------------------------------------------------------------------
  1. python:S930: 23 violations
  2. python:S3862: 15 violations
  3. python:S3923: 3 violations
  4. python:S905: 1 violations
  5. python:S1763: 1 violations

CODE_SMELL:
--------------------------------------------------------------------------------
  1. python:S1192: 212 violations
  2. python:S3776: 157 violations
  3. python:S1172: 114 violations
  4. python:S1135: 95 violations
  5. python:S117: 82 violations

SECURITY_HOTSPOT:
--------------------------------------------------------------------------------
  1. encrypt-data: 33 violations
  2. others: 22 violations
  3. weak-cryptography: 17 violations
  4. csrf: 6 violations
  5. log-injection: 4 violations

====================================================================================================
Table Data (Agents as Columns, Grouped by Issue Type):
====================================================================================================
       IssueType              Rule                                              Description  Total  Claude_Code  Claude_Code_pct  Copilot  Copilot_pct  Cursor  Cursor_pct  Devin  Devin_pct  OpenAI_Codex  OpenAI_Codex_pct
             BUG       python:S930                                Description not available     23           16        69.565217        0     0.000000       0    0.000000      0   0.000000             7         30.434783
             BUG      python:S3862                                Description not available     15            0         0.000000        4    26.666667       0    0.000000      0   0.000000            11         73.333333
             BUG      python:S3923                                Description not available      3            0         0.000000        0     0.000000       0    0.000000      0   0.000000             3        100.000000
             BUG       python:S905                                Description not available      1            0         0.000000        0     0.000000       0    0.000000      1 100.000000             0          0.000000
             BUG      python:S1763                                Description not available      1            1       100.000000        0     0.000000       0    0.000000      0   0.000000             0          0.000000
      CODE_SMELL      python:S1192                 String literals should not be duplicated    212           22        10.377358       69    32.547170      25   11.792453     33  15.566038            63         29.716981
      CODE_SMELL      python:S3776 Cognitive Complexity of functions should not be too high    157            6         3.821656       25    15.923567      53   33.757962     11   7.006369            62         39.490446
      CODE_SMELL      python:S1172             Unused function parameters should be removed    114            0         0.000000        6     5.263158      75   65.789474      2   1.754386            31         27.192982
      CODE_SMELL      python:S1135                            "TODO" tags should be handled     95            2         2.105263       16    16.842105       8    8.421053      3   3.157895            66         69.473684
      CODE_SMELL       python:S117                                Description not available     82            0         0.000000        1     1.219512      39   47.560976      0   0.000000            42         51.219512
SECURITY_HOTSPOT      encrypt-data                                Description not available     33            0         0.000000       10    30.303030       0    0.000000      7  21.212121            16         48.484848
SECURITY_HOTSPOT            others                                Description not available     22            6        27.272727        0     0.000000       0    0.000000     10  45.454545             6         27.272727
SECURITY_HOTSPOT weak-cryptography                                Description not available     17            0         0.000000        1     5.882353       1    5.882353      0   0.000000            15         88.235294
SECURITY_HOTSPOT              csrf                                Description not available      6            1        16.666667        0     0.000000       1   16.666667      0   0.000000             4         66.666667
SECURITY_HOTSPOT     log-injection                                Description not available      4            0         0.000000        0     0.000000       0    0.000000      0   0.000000             4        100.000000

====================================================================================================
LATEX CODE (Copy and paste into your paper)
====================================================================================================

\begin{table*}[t]
\centering
\caption{Top 5 Most Violated SonarQube Rules per Issue Type with Agent Distribution}
\label{tab:top5_rules_per_type}
\resizebox{\textwidth}{!}{%
\begin{tabular}{@{}lp{1.8cm}p{5cm}cccccc@{}}
\toprule
\textbf{Issue Type} & \textbf{Rule ID} & \textbf{Description} & \textbf{Total} & \textbf{Claude\_Code} & \textbf{Copilot} & \textbf{Cursor} & \textbf{Devin} & \textbf{OpenAI\_Codex} \\
\midrule
\multirow{5}{*}{BUG} & python:S930 & Description not available & 23 & 16 (69.6\%) & 0 & 0 & 0 & 7 (30.4\%) \\
 & python:S3862 & Description not available & 15 & 0 & 4 (26.7\%) & 0 & 0 & 11 (73.3\%) \\
 & python:S3923 & Description not available & 3 & 0 & 0 & 0 & 0 & 3 (100.0\%) \\
 & python:S905 & Description not available & 1 & 0 & 0 & 0 & 1 (100.0\%) & 0 \\
 & python:S1763 & Description not available & 1 & 1 (100.0\%) & 0 & 0 & 0 & 0 \\
\cline{2-9}
\multirow{5}{*}{CODE_SMELL} & python:S1192 & String literals should not be duplicated & 212 & 22 (10.4\%) & 69 (32.5\%) & 25 (11.8\%) & 33 (15.6\%) & 63 (29.7\%) \\
 & python:S3776 & Cognitive Complexity of functions should not be too high & 157 & 6 (3.8\%) & 25 (15.9\%) & 53 (33.8\%) & 11 (7.0\%) & 62 (39.5\%) \\
 & python:S1172 & Unused function parameters should be removed & 114 & 0 & 6 (5.3\%) & 75 (65.8\%) & 2 (1.8\%) & 31 (27.2\%) \\
 & python:S1135 & "TODO" tags should be handled & 95 & 2 (2.1\%) & 16 (16.8\%) & 8 (8.4\%) & 3 (3.2\%) & 66 (69.5\%) \\
 & python:S117 & Description not available & 82 & 0 & 1 (1.2\%) & 39 (47.6\%) & 0 & 42 (51.2\%) \\
\cline{2-9}
\multirow{5}{*}{SECURITY_HOTSPOT} & encrypt-data & Description not available & 33 & 0 & 10 (30.3\%) & 0 & 7 (21.2\%) & 16 (48.5\%) \\
 & others & Description not available & 22 & 6 (27.3\%) & 0 & 0 & 10 (45.5\%) & 6 (27.3\%) \\
 & weak-cryptography & Description not available & 17 & 0 & 1 (5.9\%) & 1 (5.9\%) & 0 & 15 (88.2\%) \\
 & csrf & Description not available & 6 & 1 (16.7\%) & 0 & 1 (16.7\%) & 0 & 4 (66.7\%) \\
 & log-injection & Description not available & 4 & 0 & 0 & 0 & 0 & 4 (100.0\%) \\
\bottomrule
\end{tabular}%
}
\end{table*}


✓ LaTeX table saved to: Top5_Rules_LaTeX_Table.tex

====================================================================================================
====================================================================================================
TECHNICAL DEBT ANALYSIS
====================================================================================================

Total PRs in dataset: 1210

====================================================================================================
1. EXTRACTING DEBT VALUES FROM ISSUES
====================================================================================================

Total PRs with debt data: 1210
PRs with debt > 0: 179
Total technical debt: 145.33 hours

====================================================================================================
2. DESCRIPTIVE STATISTICS - TECHNICAL DEBT BY AGENT
====================================================================================================

       Agent  N_PRs  PRs_with_Debt  Total_Debt_Hours  Mean_Hours  Median_Hours  Std_Dev  Min  Q1       Q3       Max
 Claude_Code     15              8          8.900000    0.593333      0.083333 1.311500  0.0 0.0 0.375000  4.650000
     Copilot    106             21         45.816667    0.432233      0.000000 1.875572  0.0 0.0 0.000000 14.500000
      Cursor     40              9         39.466667    0.986667      0.000000 4.788012  0.0 0.0 0.000000 29.633333
       Devin    100             25          9.950000    0.099500      0.000000 0.255604  0.0 0.0 0.020833  1.483333
OpenAI_Codex    949            116         41.200000    0.043414      0.000000 0.221078  0.0 0.0 0.000000  3.466667

✓ Saved: Technical_Debt_Statistics_by_Agent.csv

====================================================================================================
3. TECHNICAL DEBT BREAKDOWN BY ISSUE TYPE
====================================================================================================

       Agent  Bug_Debt_Hours  Code_Smell_Debt_Hours  Vulnerability_Debt_Hours  Security_Hotspot_Debt_Hours  Total_Debt_Hours   Bug_Pct  Code_Smell_Pct  Vulnerability_Pct  Security_Hotspot_Pct
 Claude_Code        2.750000               6.150000                       0.0                          0.0          8.900000 30.898876       69.101124                0.0                   0.0
     Copilot        0.333333              45.483333                       0.0                          0.0         45.816667  0.727537       99.272463                0.0                   0.0
      Cursor        0.000000              39.466667                       0.0                          0.0         39.466667  0.000000      100.000000                0.0                   0.0
       Devin        0.266667               9.683333                       0.0                          0.0          9.950000  2.680067       97.319933                0.0                   0.0
OpenAI_Codex        3.283333              37.916667                       0.0                          0.0         41.200000  7.969256       92.030744                0.0                   0.0

✓ Saved: Technical_Debt_by_Issue_Type_and_Agent.csv

====================================================================================================
4. KRUSKAL-WALLIS TEST (Non-parametric ANOVA)
====================================================================================================

H-statistic: 38.4903
p-value: 8.8769e-08

✓ Significant difference detected (p < 0.05)
  → Agents differ significantly in technical debt introduced

====================================================================================================
5. POST-HOC DUNN TEST (Pairwise Comparisons)
====================================================================================================

Dunn Test Results (p-values with Bonferroni correction):
              Claude_Code   Copilot    Cursor     Devin  OpenAI_Codex
Claude_Code      1.000000  0.007090  0.043325  0.035205      0.000054
Copilot          0.007090  1.000000  1.000000  1.000000      0.146546
Cursor           0.043325  1.000000  1.000000  1.000000      0.472086
Devin            0.035205  1.000000  1.000000  1.000000      0.003479
OpenAI_Codex     0.000054  0.146546  0.472086  0.003479      1.000000

✓ Saved: Technical_Debt_Dunn_Test.csv

====================================================================================================
6. VISUALIZATIONS
====================================================================================================

Original data points: 1210
After removing outliers: 1037
Outliers removed: 173

✓ Visualizations saved: technical_debt_analysis.png

====================================================================================================
7. KEY INSIGHTS FOR RESEARCH PAPER
====================================================================================================

▸ Highest total debt: Copilot (45.82 hours)
▸ Lowest total debt: Claude_Code (8.90 hours)
▸ Debt ratio: 5.15x

▸ Highest mean debt per PR: Cursor (0.99 hours/PR)

▸ Debt Composition by Issue Type:

  Claude_Code:
    Bug: 30.9%
    Code Smell: 69.1%
    Vulnerability: 0.0%
    Security Hotspot: 0.0%

  Copilot:
    Bug: 0.7%
    Code Smell: 99.3%
    Vulnerability: 0.0%
    Security Hotspot: 0.0%

  Cursor:
    Bug: 0.0%
    Code Smell: 100.0%
    Vulnerability: 0.0%
    Security Hotspot: 0.0%

  Devin:
    Bug: 2.7%
    Code Smell: 97.3%
    Vulnerability: 0.0%
    Security Hotspot: 0.0%

  OpenAI_Codex:
    Bug: 8.0%
    Code Smell: 92.0%
    Vulnerability: 0.0%
    Security Hotspot: 0.0%

====================================================================================================
TECHNICAL DEBT ANALYSIS COMPLETE
====================================================================================================

Files saved:
  - Technical_Debt_Statistics_by_Agent.csv
  - Technical_Debt_by_Issue_Type_and_Agent.csv
  - technical_debt_analysis.png
  - Technical_Debt_Dunn_Test.csv

====================================================================================================

```