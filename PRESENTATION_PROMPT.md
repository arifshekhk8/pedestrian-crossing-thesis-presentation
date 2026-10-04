# Claude Code brief: design the thesis defence presentation

You are a **senior academic presentation designer and scientific editor**. Rezwoan is using Claude Code to create Md. Arif Shekh's final thesis defence presentation from this repository. Take responsibility for the complete result: study the manuscript, shape a clear narrative, design and build the slides, export the PDF, and review every slide. Deliver a finished presentation, not an outline, sample, or template.

## Assignment

- **Audience:** a thesis defence committee and research audience. Slides must support a spoken presentation, with readable evidence and concise copy.
- **Format:** 16:9 widescreen, **20–25 slides total**, including title, references, backups, and closing if used.
- **Title:** **Temporal Validity and Sampling Bias in Pedestrian Crossing Prediction: A Multi-Dataset Audit and Controlled Evaluation**.
- **Presenter:** Md. Arif Shekh, Department of Computer Science and Engineering, International University of Business Agriculture and Technology (IUBAT), Dhaka, Bangladesh.
- **Supervisor:** Nusrath Tabassum. The paper's other authors are Md Abdus Samad Kamal and Kou Yamada; do not label them as supervisors.
- **Core argument:** a crossing predictor needs pre-crossing observations. Event anchoring removes crossing frames from the tested windows, yet class-dependent sampling phase remains. A phase-matched control changes the apparent benefit of ego speed and the statistical evidence for model-family differences.

The ZIP filename uses an older study title. `manuscript/final.tex` is authoritative. Do not invent a student ID, degree, defence date, university logo, or other missing identity detail.

## Read the sources before designing

1. Read the **entire active manuscript** in `manuscript/final.tex`, including its abstract, tables, captions, Discussion, Limitations, and Conclusions. Active text in red or blue revision commands counts; commented-out LaTeX does not.
2. Read `manuscript/references.bib` and inspect the original files in `manuscript/figures/`. Determine manuscript figure numbers from `final.tex`, not filenames. If feasible, compile the manuscript to confirm section, figure, and table numbers; do not edit its research content to solve a local build issue.
3. Use the manuscript as the source of truth for claims, statistics, protocols, and terminology. `manuscript/Rev.Editor comment.tex` and `manuscript/cover_letter.tex` are background only. The original ZIP in `archive/` is preserved for reference.
4. This repository contains manuscript materials, not the training implementation, checkpoints, or additional experiment outputs. Do not suggest those exist.

## Art direction and writing

Design a coherent story: **why timing matters → what was audited → how sampling was corrected → what timing difference remained → how the controlled results changed → what researchers should report**. Give each slide one clear point. Use descriptive titles; on results slides, a concise evidence-based takeaway title can help the audience understand the finding.

Use a white canvas, near-black text, one restrained navy or blue accent, and subtle grey rules. Preserve scientific colours in the source figures. Choose one professional font family and a consistent grid with generous whitespace. Aim for titles around 30–36 pt and body text around 20–26 pt; citations and labels can be smaller but must remain legible when projected. The result should look like a carefully designed research talk, not a stock template.

Choose the composition to fit the content: full-width research figures where the figure is the evidence, editable tables where exact values matter, and simple process diagrams where steps need explanation. Vary layouts across the deck without adding decorative cards, stock photos, generic icons, gradients, or flashy transitions. Align labels with what they explain. Shorten or rearrange copy before reducing font size. Do not paste manuscript paragraphs onto slides.

Keep slide text, new diagrams, tables, and equations editable. Preserve source figures at high quality and natural proportions. Never stretch an image or crop away a data panel, axis, legend, annotation, or important context. Use vector insertion for PDF figures when possible, otherwise render at high resolution. Do not invent curves, chart values, confidence intervals, or empirical images.

Use concise author–year citations on relevant slides, with full reference details in speaker notes or a compact references section if it fits the slide limit. Write clear scholarly English, define technical terms when needed, and keep speaker notes useful for Arif's delivery rather than repeating slide text.

## Content storyboard

This **25-slide outline is a content map, not a layout template**. You may combine or rearrange slides 6–8 and 14–25 to improve pacing if the final deck stays within 20–25 slides and covers every essential result. Keep slides 1–5 in this order. In Methods, show the full pipeline and explain each process **before** its corresponding source figure. The complete Figures 2, 3, and 4 must appear.

| Suggested slide | Purpose and evidence |
| --- | --- |
| 1. Title | Current full title, presenter, department/university, supervisor. A compact paper-author line is optional. |
| 2. Road safety and problem | Figure 1 and the cited global/U.S. context, followed by the specific risk of crossing frames or unequal sampling phase in nominally pre-crossing inputs. Keep years distinct. |
| 3. Research questions | Frame-level validity across PIE, JAAD, and IDD-PeD; remaining class-dependent timing and the measured value of ego speed; consistency of four model families across protocols. |
| 4. Contributions | Frame-level audit; event anchoring and training-derived phase control on PIE; box-only versus box-plus-speed comparison; repeated, statistically evaluated model-family comparison. |
| 5. Roadmap | Convert the **last active Introduction paragraph** into Related Work, Materials and Methods, Experimental Settings, Results, Discussion and Limitations, Conclusions. |
| 6–8. Related Work | Distinguish latent intention from observable action. Cover JAAD/PIE and pre-event evaluation, restricted versus rich inputs, temporal models, evaluation reliability, and the precise sampling gap. Cite actual studies in the manuscript. |
| 9. Pipeline | Show **all of Figure 2**: annotated track, pre-event window, boxes and speed, training-derived standardization, one model per run, crossing probability, and decision. |
| 10. Dataset and split process | PIE is the controlled benchmark; JAAD is a temporal audit; IDD-PeD supports audit and exploratory external evaluation. Explain PIE recording-set partitioning before window generation. |
| 11. Dataset examples | Show **all of Figure 3**, retaining PIE, JAAD, and IDD-PeD panels, blurred faces, and labels. Box colours indicate annotated outcomes, not predictions. |
| 12. Sampling process | Explain historical track-end extraction, event anchoring, phase-matched negative sampling, and the frame-level contamination check. Make the training-only source of the phase distribution clear. |
| 13. Sampling figure | Show **all of Figure 4**, both panels and both classes. Explain the 16-frame window and distinct 30–60-frame prediction horizon. |
| 14. Inputs | Explain `[x1, y1, x2, y2, v_ego]`, the 16 × 5 and 16 × 4 conditions, frame alignment, and training-derived standardization. |
| 15. Models and evaluation | Compare BiLSTM, bidirectional GRU, bidirectional vanilla RNN, and Transformer. Show shared data and evaluation; capacities and validation-selected configurations are not equal. |
| 16. Experimental settings | One readable setup slide with hardware, window/stride/horizon, split sizes, training, five seeds, validation-selected thresholds, clustered bootstrap, and Holm correction. Put secondary detail in notes. |
| 17. Temporal audit | Use `tab:temporal-audit` to compare original and corrected windows across all three datasets, keeping denominators and extraction rules explicit. |
| 18. Event-anchored models | Use `tab:model-results` to compare all four families, distinguish the leader by metric, and show the corrected architecture contrasts. |
| 19. Residual timing | Use Figure 5 to show that event anchoring removed observed crossing frames but left a class-dependent timing signal; phase matching reduced it. |
| 20. Phase-matched model results | Use `tab:phase-control` and Figure 6 to show performance under both protocols and the change in supported architecture contrasts. |
| 21. Ego-speed ablation | Use `tab:speed-phase` to compare box-only and box-plus-speed under both protocols. Distinguish descriptive mean differences from inferential comparisons. |
| 22. Qualitative demonstration | Use Figure 7 for detector → ByteTrack → tracked boxes and recorded speed → frozen within-family ensemble. Clearly label the evidence qualitative. |
| 23. Discussion | Answer the research questions. Explain why checking crossing-frame validity and checking remaining class-dependent timing are separate steps. |
| 24. Limitations and future work | Include PIE-only controlled phase comparison, incomplete timing alignment, changed eligible populations, restricted inputs, outcome versus intention, and exploratory external transfer. Use manuscript-grounded future work. |
| 25. Conclusions and questions | Three concise, evidence-bound conclusions and a simple Questions line. Do not add a filler thank-you slide. |

### Original figure map

| Manuscript figure | Source file | Handling |
| --- | --- | --- |
| Figure 1 | `manuscript/figures/fig1_pedestrian_statistics.png` | Keep global and U.S. years and contexts separate. |
| Figure 2 | `manuscript/figures/fig2_method.png` | Show the **complete** pipeline. |
| Figure 3 | `manuscript/figures/fig7_scenes.png` | Show all dataset panels; preserve blurring. |
| Figure 4 | `manuscript/figures/fig3_anchors.pdf` | Show both panels, classes, and timing relationships. `final.tex` uses this file; do not substitute `fig3_anchors__.pdf`. |
| Figure 5 | `manuscript/figures/fig4_phase_separation.png` | Show both protocols; identify the timing-distance diagnostic. |
| Figure 6 | `manuscript/figures/fig5_curves.pdf` | Keep ROC and PR labels accurate. Its areas come from five-seed probability ensembles, not the per-seed means in the tables. If the full figure is too dense, show complete selected panels and include the full figure in supporting material. |
| Figure 7 | `manuscript/figures/fig6_demo.png` | Preserve panel labels; identify the demonstration as qualitative. |

## Scientific facts to protect

- The Introduction cites approximately **1.16 million** annual road traffic deaths and says road traffic injuries are the leading cause of death for ages **5–29**. Pedestrians accounted for **23%** of global road deaths in **2021**, approximately **274,000**. Do not calculate new statistics from different reporting years.
- Exclude PIE pedestrians with crossing label −1. Use observed crossing outcome rather than `intention_prob`. Partition recording sets **before** generating windows: train on **01, 02, 04**; validate on **05, 06**; test on **03**. Keep one pedestrian's windows in one partition and retain the split across comparisons.
- Use **16 consecutive observed frames**, stride **8**, with the final observed frame **30–60 frames** before the crossing reference, about **1–2 seconds at 30 fps**. A window is contaminated if even one input frame is annotated as crossing. Do not confuse observation length with prediction horizon.
- Phase control keeps positive event-relative windows, learns the observation-to-track-end distance distribution from **positive training windows only**, and resamples feasible negative windows from it. That distance is a **diagnostic**, not a model input. The clean IDD-PeD reference is the earlier of the supplied crossing point and first annotated crossing frame.
- The quantitative models use box coordinates in original image coordinates and frame-aligned ego speed: **16 × 5** box-plus-speed versus **16 × 4** box-only. Compute channel standardization on training data and apply it unchanged to validation/test data. Appearance, pose, and scene semantics are not quantitative model inputs. JAAD lacks the synchronized ego-speed channel needed for the five-dimensional comparison.
- Main PIE sample counts are **4,906** event-anchored windows (**2,178 / 634 / 2,094** train/validation/test) and **4,520** phase-matched windows (**2,084 / 563 / 1,873**). Experiments ran on an Apple M4 MacBook Air CPU. Consult the manuscript for further setup details.
- Training uses Adam, binary cross-entropy, batch size **32**, at most **100** epochs, and early stopping after **15** epochs without validation-AUC improvement. Seeds are **42, 0, 1, 2, 3**. Select checkpoints and F1-maximizing thresholds using validation data. Report ROC-AUC, PR-AUC, F1, and descriptive accuracy. Inference uses **10,000 pedestrian-clustered bootstrap** replicates and Holm–Bonferroni correction at α = **0.05**. Tables report means and standard deviations across seed runs; statistical contrasts use probabilities averaged across those runs. Keep these summaries distinct.
- In the **audited extraction procedures**, positive-window contamination is **67.9%** for historical PIE, **93.0%** for naive JAAD, and **81.3%** for track-end IDD-PeD. Corrected PIE and JAAD sets have **0.0% observed contamination**. Direct IDD-PeD `crossing_point` leaves **29.6%** of positives contaminated; the earlier event/onset reference gives **0.0%**. These values do not describe all published uses of those datasets.
- Under event anchoring, vanilla RNN has the highest five-seed mean ROC-AUC (**0.9481 ± 0.0058**), F1 (**0.8487 ± 0.0154**), and accuracy; Transformer has the highest mean PR-AUC (**0.8964 ± 0.0188**). **7/18** architecture–metric contrasts survive Holm correction. There is no statistically supported Transformer–vanilla RNN difference for the tested AUC, PR-AUC, or F1 contrasts. No single family leads every metric.
- Observation-to-track-end distance alone gives diagnostic AUC **1.0000** under event anchoring. Phase matching reduces it to **0.7919** across the full dataset and **0.8241** on the test split. The timing separation is reduced, **not eliminated**. This diagnostic AUC is not a neural prediction score.
- After phase matching, all four full-input models have lower five-seed mean performance on every reported metric. Corrected architecture contrasts change from **7/18** to **0/18**. Lack of a supported difference does not prove equivalence; eligible populations also differ between protocols.
- Five-seed mean PR-AUC deltas (box-plus-speed minus box-only) under event anchoring / phase matching are **BiLSTM +0.2189 / −0.0206; vanilla RNN +0.1527 / −0.0188; GRU +0.1217 / +0.0049; Transformer +0.0565 / −0.0006**. Use the manuscript's deltas based on unrounded values. Inferentially, **10/12** input contrasts survive correction under event anchoring and **0/12** after phase matching across ROC-AUC, PR-AUC, and F1. The supported conclusion is that the measured contribution of speed depends on temporal sampling; it is not evidence that speed is useless or that removing it improves prediction.
- Figure 7 is a **qualitative** detector-to-prediction demonstration. Its speed association is not a separate benchmark score, causal finding, safety-system validation, or deployment claim.
- Event-relative prediction is established prior work. Present this study's contribution as auditing generated windows and testing sensitivity to the sampling protocol; do not claim a new state-of-the-art architecture or that the study invented event anchoring.
- Limitations include the PIE-only controlled phase comparison, incomplete timing alignment, changed eligible populations and possibly box scale, restricted inputs, observed crossing outcome rather than latent intention, and exploratory IDD-PeD transfer. Do not imply universal generalization or successful external transfer.

## Production workflow and deliverables

1. **Plan.** Before authoring slides, write `presentation/presentation_plan.md`. For each slide, record its purpose, key message, source figure/table/section, proposed composition, and speaker-note emphasis. Define the typography, palette, grid, and figure treatment. Confirm the slide count and content coverage.
2. **Build.** Use the tools available in your environment to produce a real, editable PowerPoint. Add useful speaker notes. Keep source/build files needed to revise the deck. Preserve the supplied manuscript files.
3. **Export and inspect.** Export a matching PDF. Render or inspect **every slide** at normal presentation size. Check readability, hierarchy, alignment, figure completeness, legends, citations, exact numbers, and scientific interpretation. Correct problems, export again, and review the changed slides.
4. **Final audit.** Confirm slides 1–5, the methods process-before-figure sequence, every core result, the 20–25 slide limit, and identical PPTX/PDF slide sequences. Record the source checks, final count, and any unresolved question in `presentation/review_notes.md`.

Commit under `presentation/`:

- `Thesis_Defence_Arif_Shekh.pptx` — complete editable deck with speaker notes.
- `Thesis_Defence_Arif_Shekh.pdf` — matching final export.
- `presentation_plan.md`, `review_notes.md`, and necessary source/build files.

The assignment is complete only when the full deck has been built, checked slide by slide, corrected, and delivered. Do not publish it outside this repository unless Arif requests that separately.
