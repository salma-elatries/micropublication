# Introduction

Depression is a prevalent and disabling non-motor symptom of
ParkinsonΓÇÖs disease (PD), affecting up to 50% of patients and
exacerbating motor and cognitive decline
([@parkinsons_foundation_depression_2026; @parkinsons_foundation_depression_2026-1]).
Its multifactorial etiology involves demographic, clinical, and
neurocognitive factors ([@cong_prevalence_2022]); however, the
underlying neural mechanisms remain poorly understood. While motor
network dysfunction in PD has been extensively characterized,
depression-related connectivity alterations, particularly within the
default mode and limbic networks
([@morgan_altered_2018; @xu_altered_2022]), remain heterogeneous. Given
this heterogeneity, we focused on large-scale resting-state networks
most consistently implicated in depression, particularly the default
mode network (DMN), because the DMN supports self-referential and
affective processing and contains hubs, notably the medial prefrontal
cortex (mPFC), that show reproducible connectivity alterations in major
depression (`\cite{}`{=latex}(Zheng et al., 2026; Zhang et al., 2024;
Sheline et al., 2009).

This study investigates resting-state connectivity as a potential marker
of depression in PD using ParkinsonΓÇÖs Progression Markers Initiative
(PPMI) data. We analyzed rs-fMRI, T1-weighted imaging, and Geriatric
Depression Scale (GDS) scores from 90 participants. Functional
connectivity was evaluated through seed-based and ROI-to-ROI approaches
focusing on 15 regions spanning the default mode (DMN), salience (SN),
and frontoparietal (FPN) networks, given their reported involvement in
depression and PD. Graph theory complements pairwise connectivity
analyses by characterizing global integration, local segregation, and
regional topology across DMN, SN, and FPN circuits (Lan et al., 2022;
van Balkom et al., 2022).

We hypothesized that depression in PD would be associated with altered
large-scale network organization, particularly within the DMN, and that
medial prefrontal cortex (mPFC)-centered connectivity alterations would
emerge as a potential marker associated with depressive symptom
severity.

# METHODS

## Data & Participants

A total of 90 participants from the [PPMI
dataset](https://www.ppmi-info.org/access-data-specimens/download-data),
supported by the Michael J. Fox Foundation for ParkinsonΓÇÖs Research
([@marek_parkinson_2011]) were categorized into Healthy Controls (CTRL),
ParkinsonΓÇÖs Disease without Depression (PDND), and ParkinsonΓÇÖs
Disease with Depression (PDD), using a Geriatric Depression Scale (GDS)
threshold of $\geq 5$ for the PDD group. Data included 3T rs-fMRI,
T1-weighted images, demographics, and clinical metrics. To address
scanner heterogeneity, we used a harmonization procedure (see
Section [9](#Supplementary material){reference-type="ref"
reference="Supplementary material"}). Acquisition parameters were
consistent across sites (TR = 2.5s, 240 volumes), with comprehensive
characteristics detailed in
Table [1](#table:participants){reference-type="ref"
reference="table:participants"} and
Table [2](#table:manufacturers){reference-type="ref"
reference="table:manufacturers"}.

::: {#table:participants}
  **Group**    **N**   **Age (mean $\pm$ SD)**   **Sex (M/F)**   **GDS (mean $\pm$ SD)**
  ----------- ------- ------------------------- --------------- -------------------------
  CTRL          32        65.67 $\pm$ 12.37          18/14                 --
  PDND          32        64.06 $\pm$ 10.52          19/13           1.03 $\pm$ 1.31
  PDD           26        62.91 $\pm$ 9.73           18/8            6.88 $\pm$ 2.29

  : Participant characteristics across groups.
:::

::: {#table:manufacturers}
  **Group**    **Siemens**   **Philips**   **GE Medical**
  ----------- ------------- ------------- ----------------
  CTRL             24             4              4
  PDND             24             4              4
  PDD              18             4              4

  : Distribution of participants across MRI scanner manufacturers.
:::

## Preprocessing and ROI Definition {#preprocessing}

Functional and anatomical MRI data were preprocessed using the default
preprocessing pipeline implemented in the CONN toolbox (CONNv25.b;
[@nieto-castanon_conn_2022]), which is widely used in functional
connectivity studies. Detailed preprocessing steps are provided in
Supplementary Material [9](#Supplementary material){reference-type="ref"
reference="Supplementary material"}.

Following preprocessing, 15 regions of interest (ROIs) spanning the
Default Mode Network (DMN), Salience Network (SN), and Frontoparietal
Network (FPN) were selected from the CONN network atlas (Table
[\[table:conn_rois\]](#table:conn_rois){reference-type="ref"
reference="table:conn_rois"}). These networks were chosen based on their
reported involvement in cognitive and emotional processing and their
relevance to non-motor symptoms in ParkinsonΓÇÖs disease
([@menon_large-scale_2011]; [@liao_networks_2021]).

::: {#15-roi}
  **Network name**               **Seed**                         **x**   **y**   **z**
  ------------------------------ ------------------------------- ------- ------- -------
  Salience network (SAL)         Mid-cingulate cortex               0      22      35
                                 Anterior insula (L)               -44     13       1
                                 Anterior insula (R)               47      14       0
                                 Rostral prefrontal cortex (L)     -35     45      27
                                 Rostral prefrontal cortex (R)     32      46      27
                                 Supramarginal gyrus (L)           -60     -39     31
                                 Supramarginal gyrus (R)           62      -35     32
  FrontoParietal network (FPN)   Lateral prefrontal cortex (L)     -43     33      28
                                 Posterior parietal cortex (L)     -46     -58     49
                                 Lateral prefrontal cortex (R)     41      38      30
                                 Posterior parietal cortex (R)     52      -52     45
  Default mode network (DMN)     Medial prefrontal cortex           1      55      -3
                                 Lateral parietal cortex (L)       -39     -77     33
                                 Lateral parietal cortex (R)       47      -67     29
                                 Posterior cingulate cortex         1      -61     38

  : CONN toolbox network region of interest (ROI) definitions
:::

*Note: Coordinates are reported in Montreal Neurological Institute (MNI)
space. L = left hemisphere; R = right hemisphere.*

[]{#15-roi label="15-roi"}

## Connectivity Analyses

Connectivity analyses were performed in two stages. An initial
seed-based connectivity (SBC) analysis was conducted in a homogeneous
subset of participants acquired using the same scanner manufacturer (16
PDD, 20 PDND) to identify connectivity differences across groups.
Subsequently, the study was extended to a larger multicenter cohort (N =
90, Table [2](#table:manufacturers){reference-type="ref"
reference="table:manufacturers"}) using ComBat harmonization (see
Supplementary Material [9.5](#harmonization){reference-type="ref"
reference="harmonization"}), where ROI-based functional connectivity and
graph analyses were performed to evaluate whether connectivity
alterations were associated with depressive symptom severity (GDS).

#### Seed-Based Connectivity Analysis

First-level seed-based connectivity maps were generated from the 15
predefined network ROIs using bivariate correlations within the CONN
toolbox (CONNv25.b [@nieto-castanon_conn_2022]), followed by Fisher-Z
transformation. At the second level, group-level connectivity
differences were evaluated using the model:

$$SBC=\beta_1(Control)+\beta_2(PDND)+\beta_3(PDD)+\beta_4(Outliers)+\epsilon$$

where *SBC* represents seed-based connectivity strength and
$\text{Control}$, $\text{PDND}$, and $\text{PDD}$ serve as indicator
variables for each diagnostic category, and $\text{Outliers}$ accounts
for the quality assurance covariate of excluded subjects. Differences
across seeds were assessed using a multivariate omnibus F-test.
Statistical significance was defined at voxel-level $p<0.001$ and
cluster-level FDR correction ($p_{FDR}<0.05$) based on Gaussian Random
Field theory. Detailed steps are provided in Supplementary Material
[9.3](#SBC){reference-type="ref" reference="SBC"}.

#### Functional Connectivity Analysis

ROI-based functional connectivity matrices were estimated using Pearson
correlations between the predefined network ROIs and Fisher-Z
transformed prior to harmonization. Associations between connectivity
and depressive symptom severity were evaluated using generalized linear
models implemented in Python
([Statsmodels](https://www.statsmodels.org/stable/api.html)):

$$FC_{ROI}=\beta_0+\beta_1(GDS)+\beta_2(Sex)+\beta_3(Age)+\epsilon$$

where *FC$_{ROI}$* represents ROI-to-ROI functional connectivity values
and *GDS* denotes depressive symptom severity. Multiple comparisons were
controlled using FDR correction ($p_{FDR}<0.05$). Graph-theoretical
measures were subsequently derived from the harmonized connectivity
matrices.

#### Graph-Theoretical Analysis

Subject-level weighted connectivity matrices served as inputs to
construct undirected weighted graphs across the 15 ROIs. They were
converted to absolute weighted matrices, and diagonal elements were set
to zero. Following standard graph theory approaches
([@bullmore_complex_2009; @rubinov_complex_2010]; see Supplementary
Material [9.6](#graph_theory){reference-type="ref"
reference="graph_theory"}) using BCTpy-0.6.1 (Brain Connectivity
Toolbox). Graphs were thresholded across densities from 0.10 to 0.30 in
steps of 0.05 and area under the curve (AUC) values were computed across
densities for all metrics. The analysis contained global metrics,
including weighted strength, clustering coefficient, global efficiency,
and betweenness centrality and local metrics, including nodal strength,
clustering coefficient, betweenness centrality, participation
coefficient, and within-module strength z-score to characterize regional
connectivity patterns ([@sporns_graph_2018]). Group comparisons were
performed using MannΓÇôWhitney U tests with FDR correction.

# Results and Discussion

Figure [5](#fig:combined_results){reference-type="ref"
reference="fig:combined_results"} summarizes the main findings.
Seed-based connectivity analysis revealed significant group-level
differences between PDD and PDND, identifying four clusters of altered
connectivity involving the left superior parietal lobule (SPL), medial
prefrontal cortex (mPFC)/dorsal anterior cingulate cortex (dACC), right
middle temporal gyrus (MTG), and right supramarginal gyrus (SMG) (Figure
[1](#fig:seed_clusters){reference-type="ref"
reference="fig:seed_clusters"}; Table
[\[tab:sbc_results\]](#tab:sbc_results){reference-type="ref"
reference="tab:sbc_results"}). The primary cluster was located in the
left intraparietal sulcus (IPS)/SPL (cluster size $k=209$,
$p_{FDR}=0.001890$), while the remaining clusters involved mPFC/dACC
($k=101$), MTG ($k=97$), and SMG ($k=96$; all $p_{FDR}=0.028392$).

These findings suggest altered large-scale connectivity involving the
DMN, salience, and frontoparietal networks in PDD. Altered mPFC/dACC
connectivity, regions implicated in self-referential and emotional
processing ([@levorsen_decomposing_2025; @yun_functional_2022]), may
reflect depression-related network alterations previously reported in
Parkinsonian populations ([@su_altered_2022; @liao_networks_2021]).
Altered IPS and SMG connectivity may further indicate frontoparietal
reorganization associated with disrupted basal ganglia-thalamocortical
circuitry ([@liu_resting-state_2022]).

ROI-based functional connectivity analysis identified convergent
alterations within key DMN connections, including mPFCΓÇôleft LP,
mPFCΓÇôright LP, and mPFCΓÇôPCC (Figure
[3](#fig:dmn_brain){reference-type="ref" reference="fig:dmn_brain"};
Table [\[tab:fc_results\]](#tab:fc_results){reference-type="ref"
reference="tab:fc_results"}). All associations showed negative beta
coefficients, indicating reduced DMN connectivity with increasing
depressive symptom severity (GDS). Although these findings did not
survive multiple comparison correction, they were further explored due
to their consistency with previous studies reporting reduced DMN
connectivity in major depressive disorder and recurrent depression
([@tozzi_reduced_2021; @yan_reduced_2019]).

Graph based analysis provided a complementary evaluation of network
topology across DMN, SN and FPN. None of the global metrics showed
significance; however, exploratory nodal effects were observed in left
frontoparietal posterior parietal cortex, right DMN lateral parietal
cortex and DMN mPFC (see figure 1 and Table
[\[tab:graph_results\]](#tab:graph_results){reference-type="ref"
reference="tab:graph_results"}), indicating possible alterations in
cross-network participation, local segregation, and within-module
integration. Although these effects did not survive FDR correction,
their regional distribution aligns with previous findings demonstrating
a connection to the DMN and FPN being positively related to depressive
symptoms in PD, as well as altered FPN modular organization in
depression. (Wei et al., 2017; Han et al., 2011; Lan et al., 2022)

Based on the convergent SBC, ROI-based, and graph theory findings
centered on the mPFC, a composite DMN connectivity score (DMN marker)
was constructed to further explore DMN alterations associated with
depressive symptoms. Significant group differences ($p<0.05$) were
observed between PDD and control subjects, showing a progressive
decrease in DMN connectivity across groups (Figure
[4](#fig:dmn_scores){reference-type="ref" reference="fig:dmn_scores"};
Table
[\[tab:dmn_score_results\]](#tab:dmn_score_results){reference-type="ref"
reference="tab:dmn_score_results"}). These findings suggest that
mPFC-centered DMN connectivity may represent a potential marker
associated with depression in ParkinsonΓÇÖs disease, consistent with the
established role of the mPFC in emotional processing and stress-related
responses ([@pizzagalli_prefrontal_2022; @bittar_functional_2021]).

<figure id="fig:combined_results">
<figure id="fig:seed_clusters">
<img src="final-sbc-2.png" style="width:80.0%" />
<figcaption aria-hidden="true"></figcaption>
</figure>
<figure id="fig:dmn_brain">
<img src="FUNCTIONALCONNECTIVITY.png" />
<figcaption aria-hidden="true"></figcaption>
</figure>
<figure id="fig:dmn_brain">
<img src="barplot.png" />
<figcaption aria-hidden="true"></figcaption>
</figure>
<figure id="fig:dmn_scores">
<img src="boxplot.png" style="width:80.0%" />
<figcaption aria-hidden="true"></figcaption>
</figure>
<figcaption> Overview of mPFC-centered connectivity analyses. Top:
Seed-based connectivity results showing significant clusters; color bar
denotes <span class="math inline"><em>F</em></span>-values (<span
class="math inline"><em>F</em>(14, 714)</span>) ranging from 2.62 to
4.18. Middle: DMN connectivity patterns centered on mPFC. Bottom left:
Graph theory results showing significant ROIs. Bottom right:
distribution of DMN connectivity scores across CTRL, PD and PDD groups.
</figcaption>
</figure>

::: {#tab:combined_results}
   **Cluster (coord)**   **Size (k)**   **$p_{unc}$**   **$p_{FDR}$**
  --------------------- -------------- --------------- ---------------
     $-36\ -66\ +54$         209          0.000040        0.001890
     $-02\ +26\ +32$         101          0.001964        0.028392
     $+36\ -60\ +18$          97          0.002317        0.028392
     $+66\ -32\ +40$          96          0.002416        0.028392

  :  Summary of connectivity analyses comparing CTRL, PDND, and PDD
  groups.
:::

::: {#tab:combined_results}
                         **ROI (coord)**                          **$\beta$**   **$p_{unc}$**   **$p_{FDR}$**
  -------------------------------------------------------------- ------------- --------------- ---------------
   DMN.MPFC $(1,55,-3)$ $\rightarrow$ DMN.LP (L) $(-39,-77,33)$    -0.023332      0.011707        0.892914
   DMN.MPFC $(1,55,-3)$ $\rightarrow$ DMN.LP (R) $(47,-67,29)$     -0.021428      0.033765        0.892914
     DMN.MPFC $(1,55,-3)$ $\rightarrow$ DMN.PCC $(1,-61,38)$       -0.023941      0.036295        0.892914

  :  Summary of connectivity analyses comparing CTRL, PDND, and PDD
  groups.
:::

::: {#tab:combined_results}
  **Metric**                       **ROI (coord)**                **Effect Size**   **$p_{unc}$**   **$p_{FDR}$**       
  -------------------------------- ---------------------------- ----------------- --------------- --------------- -- -- --
  Nodal participation              DMN.LP (R) $(47,-67,29)$             -0.021308        0.032826        0.492393       
  Nodal clustering                 FPN.PPC (L) $(-46,-58,49)$            0.019115        0.040591        0.522919       
  Within-module strength z-score   DMN.MPFC $(1,55,-3)$                 -0.011111        0.048238        0.723570       

  :  Summary of connectivity analyses comparing CTRL, PDND, and PDD
  groups.
:::

::: {#tab:combined_results}
   **Comparison**      **Test**       **$p$**
  ---------------- ----------------- ---------
       Global       Kruskal--Wallis   0.0108
    CTRL vs PDD        Post-hoc       0.0043
    CTRL vs PDND       Post-hoc       0.0897
    PDND vs PDD        Post-hoc       0.1023

  :  Summary of connectivity analyses comparing CTRL, PDND, and PDD
  groups.
:::

# Conclusion {#conclussion}

[]{#conclussion_geetha label="conclussion_geetha"}

Seed-based analysis revealed significant functional connectivity
differences between PDD and PDND within DMN and frontoparietal regions
in a homogeneous Siemens cohort. Extending this analysis to a larger
multicenter cohort through harmonization revealed convergent trends in
mPFC-centered DMN connectivity, demonstrating a negative association
between depressive symptom severity (GDS) and connectivity measures.
Graph-theoretical analysis supported this pattern at the regional level,
showing exploratory nodal alterations in DMN and frontoparietal regions
without corrected global topology differences. Furthermore, exploration
using a composite DMN connectivity score demonstrated a progressive
decrease in connectivity across groups, significantly differentiating
PDD from control subjects.

Collectively, these findings reveal convergent evidence across
seed-based, ROI-based, graph theory, and composite connectivity
analyses, highlighting mPFC-centered DMN alterations as a potential
marker of depression in ParkinsonΓÇÖs disease. The progressive reduction
of DMN connectivity across groups further supports the critical
involvement of large-scale network dysfunction in depression-related
processes in PD.

# Acknowledgment

We thank the Neuromatch Impact Scholar Programme, the Michael J. Fox
Foundation, and the ParkinsonΓÇÖs Progression Markers Initiative (PPMI)
for supporting this work and providing access to the dataset.

# Author Contributions

Geetha Iyer performed the seed-based connectivity analyses. Rosario
Huaranca conducted the ROI-to-ROI connectivity analyses. Salma Elatries
performed the graph-theoretical analyses. Abdul Rauf Anwar supervised
the project. All authors contributed to interpretation, manuscript
preparation, and final approval.

# Data Availability Statement

The data used in this study were obtained from the ParkinsonΓÇÖs
Progression Markers Initiative (PPMI) database (available at
www.ppmi-info.org/data). The datasets are publicly and freely available
to qualified investigators upon completing an online application,
signing the Data User Agreement, and complying with the study's
publication policies. Because the terms of the Data User Agreement
strictly prohibit the unauthorized distribution of participant-level
data, the authors cannot share the raw data files directly.

# Appendix {#Appendices}

::: {#table:fc_ctrl_pdd}
  **ROI 1**   **MNI (x,y,z)**   **ROI 2**     **MNI (x,y,z)**   **Network Interaction**   **p-value**    **Direction (PDD vs CTRL)**
  ----------- ----------------- ------------- ----------------- ------------------------- ------------- -----------------------------
  MPFC        (1,55,-3)         LP (L)        (-39,-77,33)      DMN--DMN                  0.0316                $\downarrow$
  MPFC        (1,55,-3)         LP (R)        (47,-67,29)       DMN--DMN                  0.0292                $\downarrow$
  MPFC        (1,55,-3)         SMG (L)       (-60,-39,31)      DMN--Salience             0.0280                $\downarrow$
  LP (R)      (47,-67,29)       AInsula (L)   (-44,13,1)        DMN--Salience             0.0479                $\downarrow$
  LP (R)      (47,-67,29)       RPFC (R)      (32,46,27)        DMN--Salience             0.0229                $\downarrow$
  LP (R)      (47,-67,29)       SMG (L)       (-60,-39,31)      DMN--Salience             0.0126                $\downarrow$
  LP (R)      (47,-67,29)       LPFC (R)      (41,38,30)        DMN--FPN                  0.0055                $\downarrow$
  RPFC (L)    (-32,45,27)       SMG (L)       (-60,-39,31)      Salience--Salience        0.0479                 $\uparrow$

  : Functional connectivity differences for CTRL vs PDD (uncorrected
  $p < 0.05$).
:::

Arrows indicate direction relative to CTRL: $\uparrow$ increased
connectivity in PDD (PDD $>$ CTRL), $\downarrow$ decreased connectivity
in PDD (PDD $<$ CTRL).

::: {#table:fc_pdnd_pdd}
  **ROI 1**      **MNI**     **ROI 2**     **MNI**         **Network**       **p-value**   **Direction (PDD vs PDND)**
  ----------- ------------- ----------- -------------- -------------------- ------------- -----------------------------
  MPFC          (1,55,-3)     LP (L)     (-39,-77,33)        DMN--DMN          0.0328             $\downarrow$
  RPFC (L)     (-32,45,27)    SMG (L)    (-60,-39,31)   Salience--Salience     0.0316              $\uparrow$

  : Functional connectivity differences for PDND vs PDD (uncorrected
  $p < 0.05$).
:::

Arrows indicate direction relative to PDND: $\uparrow$ increased
connectivity in PDD (PDD $>$ PDND), $\downarrow$ decreased connectivity
in PDD (PDD $<$ PDND).

::: {#table:dfc_ctrl_pdd}
  **ROI 1**   **MNI (x,y,z)**   **ROI 2**     **MNI (x,y,z)**   **Network Interaction**   **p-value**    **Direction (PDD vs CTRL)**
  ----------- ----------------- ------------- ----------------- ------------------------- ------------- -----------------------------
  MPFC        (1,55,-3)         LP (R)        (47,-67,29)       DMN--DMN                  0.0369                $\downarrow$
  MPFC        (1,55,-3)         SMG (L)       (-60,-39,31)      DMN--Salience             0.0045                $\downarrow$
  LP (L)      (-39,-77,33)      AInsula (R)   (47,14,0)         DMN--Salience             0.0239                $\downarrow$
  LP (R)      (47,-67,29)       ACC           (0,22,35)         DMN--Salience             0.0328                $\downarrow$
  LP (R)      (47,-67,29)       AInsula (R)   (47,14,0)         DMN--Salience             0.0383                $\downarrow$
  LP (R)      (47,-67,29)       RPFC (L)      (-32,45,27)       DMN--Salience             0.0067                $\downarrow$
  LP (R)      (47,-67,29)       RPFC (R)      (32,46,27)        DMN--Salience             0.0106                $\downarrow$
  LP (R)      (47,-67,29)       SMG (L)       (-60,-39,31)      DMN--Salience             0.0178                $\downarrow$
  LP (R)      (47,-67,29)       SMG (R)       (62,-35,32)       DMN--Salience             0.0328                $\downarrow$
  LP (R)      (47,-67,29)       LPFC (R)      (41,38,30)        DMN--FPN                  0.0043                $\downarrow$
  ACC         (0,22,35)         AInsula (L)   (-44,13,1)        Salience--Salience        0.0220                $\downarrow$

  : Dynamic functional connectivity differences for CTRL vs PDD
  (uncorrected $p < 0.05$).
:::

Arrows indicate direction relative to CTRL: $\uparrow$ increased
variability in PDD (PDD $>$ CTRL), $\downarrow$ decreased variability in
PDD (PDD $<$ CTRL).

::: {#table:dfc_pd_pdd}
  **ROI 1**   **MNI (x,y,z)**   **ROI 2**   **MNI (x,y,z)**   **Network Interaction**   **p-value**    **Direction (PDD vs PDND)**
  ----------- ----------------- ----------- ----------------- ------------------------- ------------- -----------------------------
  LP (R)      (47,-67,29)       LPFC (R)    (41,38,30)        DMN--FPN                  0.0369                $\downarrow$
  RPFC (L)    (-32,45,27)       PPC (L)     (-46,-58,49)      Salience--FPN             0.0445                 $\uparrow$

  : Dynamic functional connectivity differences for PDND vs PDD
  (uncorrected $p < 0.05$).
:::

Arrows indicate direction relative to PDND: $\uparrow$ increased
variability in PDD (PDD $>$ PDND), $\downarrow$ decreased variability in
PDD (PDD $<$ PDND).

::: {#table:gc_pd_pdd}
  **Source ROI**   **MNI (x,y,z)**   **Target ROI**   **MNI (x,y,z)**   **Network Interaction**           **p-value**    **Direction (PDD vs PDND)**
  ---------------- ----------------- ---------------- ----------------- --------------------------------- ------------- -----------------------------
  AInsula (R)      (47,14,0)         RPFC (R)         (32,46,27)        Salience $\rightarrow$ Salience   0.0032                 $\uparrow$
  RPFC (L)         (-32,45,27)       AInsula (L)      (-44,13,1)        Salience $\rightarrow$ Salience   0.0341                 $\uparrow$
  PPC (R)          (52,-52,45)       PCC              (1,-61,38)        FPN $\rightarrow$ DMN             0.0202                $\downarrow$

  : Differences in directed functional connectivity (Granger causality)
  between PDND and PDD (uncorrected $p < 0.05$).
:::

Arrows indicate direction of change relative to PD: $\uparrow$ increased
causal influence in PDD (PDD $>$ PDND), $\downarrow$ decreased influence
in PDD (PDD $<$ PDND).

::: {#table:gc_ctrl_pdd}
  **Source ROI**   **MNI (x,y,z)**   **Target ROI**   **MNI (x,y,z)**   **Network Interaction**      **p-value**    **Direction (CTRL vs PDD)**
  ---------------- ----------------- ---------------- ----------------- ---------------------------- ------------- -----------------------------
  LP (L)           (-39,-77,33)      AInsula (L)      (-44,13,1)        DMN $\rightarrow$ Salience   0.0269                 $\uparrow$
  PPC (R)          (52,-52,45)       LP (L)           (-39,-77,33)      FPN $\rightarrow$ DMN        0.0497                $\downarrow$

  : Differences in directed functional connectivity (Granger causality)
  between CTRL and PDD (uncorrected $p < 0.05$).
:::

Arrows indicate direction of change relative to PD: $\uparrow$ increased
causal influence in PDD (PDD $>$ CTRL), $\downarrow$ decreased influence
in PDD (PDD $<$ CTRL).

::: {#tab:appendix_global_metrics}
  **Comparison**   **Metric**     **U**   **$p_{\mathrm{raw}}$**   **$p_{\mathrm{FDR}}$**   **FDR sig.**
  ---------------- ------------- ------- ------------------------ ------------------------ --------------
  Ctrl vs PDND     betweenness    438.0          0.323694                 0.994643               No
  Ctrl vs PDND     strength       548.0          0.633601                 0.994643               No
  Ctrl vs PDND     clustering     528.0          0.835135                 0.994643               No
  Ctrl vs PDND     efficiency     511.0          0.994643                 0.994643               No
  Ctrl vs PDD      clustering     400.0          0.808513                 1.000000               No
  Ctrl vs PDD      efficiency     427.0          0.869598                 1.000000               No
  Ctrl vs PDD      betweenness    422.0          0.931472                 1.000000               No
  Ctrl vs PDD      strength       416.0          1.000000                 1.000000               No

  : Global graph metrics from the graph-theoretical analysis for
  depression-focused comparisons.
:::

*Note: Global metrics were computed on the 15-ROI ComBat-harmonized
network. Pairwise group comparisons were performed using two-sided
Mann--Whitney U tests. No global metric reached statistical significance
after FDR correction.*

[]{#tab:appendix_global_metrics label="tab:appendix_global_metrics"}

# Supplementary Material {#Supplementary material}

## **Preprocessing** {#preprocessing-1}

Functional and anatomical data were preprocessed using a modular
preprocessing pipeline including realignment with correction of
susceptibility distortion interactions, slice timing correction, outlier
detection, direct coregistration to structural, direct segmentation and
MNI-space normalization, and smoothing. Functional data were realigned
using SPM realign & unwarp procedure, where all scans were coregistered
to a reference image (first scan of the first session) using a least
squares approach and a 6 parameter (rigid body) transformation and
resampled using b-spline interpolation to correct for motion and
magnetic susceptibility interactions. Temporal misalignment between
different slices of the functional data (acquired in interleaved Siemens
order) was corrected following SPM slice-timing correction (STC)
procedure, using Sinc temporal interpolation to resample each slice BOLD
timeseries to a common mid-acquisition time. Potential outlier scans
were identified using Artifact detection tools (ART) as acquisitions
with framewise displacement above 0.9 mm or global BOLD signal changes
above 5 standard deviations, and a reference BOLD image was computed for
each subject by averaging all scans excluding outliers. Functional and
anatomical data were coregistered using SPM intermodality coregistration
procedure with a normalized mutual information objective
function.Functional and anatomical data were normalized into standard
MNI space, segmented into grey matter, white matter, and cerebrospinal
fluid (CSF) tissue classes, and resampled to 2 mm isotropic voxels
following a direct normalization procedure using SPM unified
segmentation and normalization algorithm with the default IXI-549 tissue
probability map template
([@ashburner_fast_2007; @ashburner_unified_2005]). Lastly, functional
data were smoothed using spatial convolution with a Gaussian kernel of 8
mm full width half maximum (FWHM).

## **Denoising**

In addition, functional data were denoised using a confound regression
pipeline incorporating established nuisance regressors. This included
the removal of potential confounding effects derived from white matter
(5 regressors), CSF (5 regressors), motion parameters and their
first-order derivatives (12 regressors), outlier scans (\<16
regressors), session effects and their first-order derivatives (2
regressors), and linear trends (2 regressors) within each functional
run, followed by bandpass frequency filtering of the BOLD timeseries
between 0.01 Hz and 0.08 Hz. Component-based noise correction (CompCor)
regressors were estimated within each subject's eroded white matter and
CSF masks by extracting the mean signal and the largest principal
components orthogonal to the mean signal, motion parameters, and outlier
scans. Based on the number of nuisance regressors included, the
effective temporal degrees of freedom of the denoised BOLD signal ranged
from 69.3 to 74.9 (mean 74.3) across subjects.

## **Seed-Based Connectivity Analysis** {#SBC}

Seed-based connectivity maps (SBC) were estimated characterizing the
spatial pattern of functional connectivity with a seed area. Seed
regions included 15 High-Performance Computing Independent Component
Analysis (HPC-ICA) network ROIs. Functional connectivity strength was
represented by Fisher-transformed bivariate correlation coefficients
from a weighted general linear model (weighted-GLM), estimated
separately for each seed area and target voxel, modeling the association
between their BOLD signal timeseries. In order to compensate for
possible transient magnetization effects at the beginning of each run,
individual scans were weighted by a step function convolved with an SPM
canonical hemodynamic response function and rectified.

Group-level analyses were performed using a General Linear Model (GLM).
For each individual voxel a separate GLM was estimated, with first-level
connectivity measures at this voxel as dependent variables (one
independent sample per subject and one measurement per task or
experimental condition, if applicable), and groups or other
subject-level identifiers as independent variables. Voxel-level
hypotheses were evaluated using multivariate parametric statistics with
random-effects across subjects and sample covariance estimation across
multiple measurements. Inferences were performed at the level of
individual clusters (groups of contiguous voxels). Cluster-level
inferences were based on parametric statistics from Gaussian Random
Field theory. Results were thresholded using a combination of a
cluster-forming p \< 0.001 voxel-level threshold, and a familywise
corrected p-FDR \< 0.05 cluster-size threshold.

## Effective Connectivity: Granger Causality Model {#sm: EC}

Granger causality was computed within a multivariate vector
autoregressive (VAR) framework ([@deshpande_investigating_2012]):

$$X(t) = \sum_{n=1}^{p} A(n)\,X(t-n) + E(t)
\label{eq3}$$

where $X(t)$ denotes the multivariate time series, $A(n)$ are the
coefficient matrices at lag $n$, $p$ is the model order, and $E(t)$ is
the residual error term.

The estimated VAR model was transformed into an autocovariance
representation, from which pairwise-conditional Granger causality was
derived. This formulation enables the estimation of directed
interactions between regions while conditioning on the activity of all
other variables in the system.

## Harmonization

Harmonization was applied to reduce scanner-related variability in this
multicenter dataset, ensuring that observed differences reflect
biological rather than acquisition-related effects. In this study,
harmonization was performed using the ComBat method, which corrects for
systematic site-related differences in feature distributions while
preserving biological variability ([@orlhac_guide_2022]). ComBat models
the observed signal as a combination of biological effects and additive
and multiplicative scanner effects:
$$y_{ij} = \alpha + \gamma_i + \delta_i \epsilon_{ij} \label{eq1}$$
where $y_{ij}$ denotes the feature value for subject $j$ at site $i$,
$\alpha$ is the global mean, $\gamma_i$ and $\delta_i$ represent
additive and multiplicative site effects, and $\epsilon_{ij}$ is the
residual error. Using a Bayesian framework, these site effects are
estimated and removed to obtain harmonized values:
$$y_{ij}^{\text{ComBat}} = \frac{y_{ij} - \hat{\alpha} - \hat{\gamma}_i}{\hat{\delta}_i} + \hat{\alpha} \label{eq2}$$
where $\hat{\alpha}$, $\hat{\gamma}_i$, and $\hat{\delta}_i$ are the
estimated parameters. Harmonization was applied to the extracted
features (e.g., connectivity measures), and the resulting data were used
for subsequent statistical analyses. Implementation was performed using
the [NeuroHarmonize Python
toolbox](https://pypi.org/project/neuroHarmonize/)
([@pomponio_rpomponioneuroharmonize_2026]).

## **Graph Theory** {#graph_theory}

The resulting ROI-to-ROI connectivity matrices which were harmonized
were used as input. The diagonal elements of these matrices were set to
zero and, although using absolute edge weights, undirected, weighted
graphs were constructed using absolute edge weights which provide a
measure of the magnitude of functional coupling, regardless of the
correlation direction. This is important, since all of the graph metrics
used in this study assume a network is weighted non-negatively.
[@rubinov_complex_2010].

Graph-theoretical analysis was conducted using BCTpy-0.6.1
[@roan_laplante_bctpy_nodate]. Graphs were proportionally thresholded
across densities from 0.10 to 0.30 in steps of 0.05, and area under the
curve values were computed across thresholds using trapezoidal
integration. The metrics listed in the main methods were selected to
characterize overall connectivity, integration, segregation, centrality,
cross-network participation, and within-network integration.

Global metrics included weighted strength, clustering coefficient,
global efficiency, and betweenness centrality. Local metrics included
nodal strength, nodal clustering coefficient, nodal betweenness
centrality, participation coefficient, and within-module strength
z-score. The participation coefficient measured the level of
cross-network integration, while the z-score of the within-module
strength measured the strength of connection between each ROI found
within its assigned module when compared to other ROIs in that module.
For module-based metrics, module labels were predefined according to the
CONN atlas assignments: DMN, salience network, and frontoparietal
network.

Global weighted strength was calculated as:

$$S^{w} = \frac{1}{N} \sum_{i=1}^{N} \sum_{j=1}^{N} w_{ij}
\label{eq:global_strength}$$

where $S^{w}$ denotes global weighted strength, $w_{ij}$ is the edge
weight between nodes $i$ and $j$, and $N$ is the total number of nodes.

The weighted clustering coefficient was calculated as:

$$C^{w} = \frac{1}{N} \sum_{i=1}^{N} \frac{1}{k_i (k_i - 1)} \sum_{j,h} (w_{ij} w_{ih} w_{jh})^{1/3}
\label{eq:global_clustering}$$

where $C^{w}$ is the global clustering coefficient and $k_i$ is the
degree of node $i$.

Global efficiency was calculated as:

$$E_{glob} = \frac{1}{N(N-1)} \sum_{i \neq j} \frac{1}{d_{ij}}
\label{eq:global_efficiency}$$

where $E_{glob}$ represents global efficiency and $d_{ij}$ is the
shortest path length between nodes $i$ and $j$.

Global betweenness centrality was calculated as the average nodal
betweenness centrality:

$$BC = \frac{1}{N} \sum_{i=1}^{N} \sum_{s \neq i \neq t} \frac{\sigma_{st}(i)}{\sigma_{st}}
\label{eq:global_betweenness}$$

where $\sigma_{st}$ is the number of shortest paths between nodes $s$
and $t$, and $\sigma_{st}(i)$ is the number of those paths passing
through node $i$.

The same thresholding and AUC procedure was used for local graph
metrics. Nodal strength was calculated as:

$$s_i^{w} = \sum_{j=1}^{N} w_{ij}
\label{eq:nodal_strength}$$

where $s_i^{w}$ is the weighted strength of node $i$.

Nodal clustering coefficient was calculated as:

$$C_i^{w} = \frac{1}{k_i (k_i - 1)} \sum_{j,h} (w_{ij} w_{ih} w_{jh})^{1/3}
\label{eq:nodal_clustering}$$

where $C_i^{w}$ is the clustering coefficient of node $i$.

Nodal betweenness centrality was calculated as:

$$BC_i = \sum_{s \neq i \neq t} \frac{\sigma_{st}(i)}{\sigma_{st}}
\label{eq:nodal_betweenness}$$

where $BC_i$ is the betweenness centrality of node $i$.

Participation coefficient was calculated to characterize cross-network
integration:

$$P_i = 1 - \sum_{m=1}^{M} \left(\frac{s_{i,m}^{w}}{s_i^{w}}\right)^2
\label{eq:participation}$$

where $P_i$ is the participation coefficient of node $i$, $s_{i,m}^{w}$
is the strength of connections from node $i$ to module $m$, $s_i^{w}$ is
the total nodal strength, and $M$ is the number of predefined modules.
Modules corresponded to the DMN, salience network, and frontoparietal
network.

Within-module strength z-score was calculated to characterize
within-network integration:

$$z_i = \frac{s_{i,m_i}^{w} - \mu_{m_i}}{\sigma_{m_i}}
\label{eq:within_module_z}$$

where $z_i$ is the within-module strength z-score of node $i$,
$s_{i,m_i}^{w}$ is the within-module strength of node $i$ within its
assigned module $m_i$, and $\mu_{m_i}$ and $\sigma_{m_i}$ are the mean
and standard deviation of within-module strengths within module $m_i$.

This set of metrics was selected to characterize complementary aspects
of brain network organization, including overall connectivity,
integration, segregation, centrality, cross-network participation, and
within-network integration.

Pairwise group comparisons were performed using two-sided MannΓÇôWhitney
U tests. BenjaminiΓÇôHochberg FDR correction was applied across metrics
within each pairwise comparison.
