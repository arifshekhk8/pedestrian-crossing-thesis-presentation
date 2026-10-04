# Thesis defence presentation brief for Rezwoan

## Assignment

Rezwoan, create the complete main presentation for Md. Arif Shekh's thesis final defence from the manuscript supplied in this repository. Produce finished, editable slides, not only an outline or a design sample.

Use the current manuscript title:

**Temporal Validity and Sampling Bias in Pedestrian Crossing Prediction: A Multi-Dataset Audit and Controlled Evaluation**

The ZIP filename contains an earlier title. The active title and content in **manuscript/final.tex** are authoritative.

Aim for **20–25 slides in total, including the title and any closing, reference, or backup slides**. The recommended plan below uses 25 slides. Keep the required first five slides and the required method-slide sequence. Adjust later slides only when this improves explanation or readability without removing essential evidence.

Use a **white background and a professional academic research presentation style** suitable for a thesis defence or journal research talk. Write clear, precise, easy-to-understand scholarly English.

## Read the sources before designing

1. Read the complete active manuscript in manuscript/final.tex, from the abstract through Conclusions.
2. Read manuscript/references.bib for the actual references and citation metadata.
3. Inspect the original files in manuscript/figures/.
4. Treat active text inside red or blue revision commands as manuscript content. Ignore commented-out text beginning with an unescaped percent sign. Do not display revision colours as slide styling.
5. Use manuscript/Rev.Editor comment.tex and manuscript/cover_letter.tex only as background if necessary. They are not the presentation's main source.
6. Do not assume that figures are numbered according to their filenames. Their order in final.tex determines their manuscript numbers.
7. If compiling the manuscript is feasible, confirm the resolved section, figure, and table numbers from the compiled output. Do not edit the manuscript to solve a local compilation problem.

The repository contains manuscript materials, not the full experimental implementation. Do not invent implementation details or claim that code, trained checkpoints, or additional experiment outputs are available.

### Figure map for this manuscript version

| Manuscript figure | File relative to manuscript/ | Subject | Main-slide use |
| --- | --- | --- | --- |
| Figure 1 | figures/fig1_pedestrian_statistics.png | Global and U.S. pedestrian fatality statistics | Slide 2 |
| Figure 2 | figures/fig2_method.png | Complete prediction pipeline | Slide 9, complete figure |
| Figure 3 | figures/fig7_scenes.png | Annotated PIE, JAAD, and IDD-PeD scenes | Slide 11, complete figure |
| Figure 4 | figures/fig3_anchors.pdf | Historical track-end extraction and event anchoring with phase matching | Slide 13, complete figure |
| Figure 5 | figures/fig4_phase_separation.png | Class-dependent temporal position before and after phase matching | Slide 19 |
| Figure 6 | figures/fig5_curves.pdf | ROC and precision–recall curves under both protocols | Slide 20 |
| Figure 7 | figures/fig6_demo.png | Qualitative detector-to-prediction demonstration | Slide 22 |

Use figures/fig3_anchors.pdf because final.tex includes that file. Do not substitute figures/fig3_anchors__.pdf.

## Mandatory workflow: plan, build, inspect, revise

**First create a proper plan. Then follow it. Recheck every slide before delivery.**

Before authoring the deck, write presentation/presentation_plan.md. For each planned slide, record its number, title, short section label, purpose, intended content, source section, figure or table, layout, and speaker-note emphasis. Confirm the total count and coverage before building. Planning is a working step, not the final deliverable.

Build all main slides from that plan. Use the supplied research figures and editable text, equations, tables, and data charts where possible. Add useful speaker notes that explain the method and findings in simple English without merely reading the slide.

Render or export the deck and inspect every slide at normal presentation size. Check both visual layout and scientific accuracy. Correct problems, export again, and inspect the revised slides. The final PPTX and PDF must contain the same final slide sequence.

Do not stop after producing a plan, a few sample slides, or an unfinished template.

## Required slide plan

### Slide 1 — Title and presenter information

Section label: **Thesis Defence**

Include the full current manuscript title, **Presenter: Md. Arif Shekh**, Department of Computer Science and Engineering, and **International University of Business Agriculture and Technology (IUBAT), Dhaka, Bangladesh**. Include **Supervisor: Nusrath Tabassum** using the correct spelling.

The manuscript authors are Md. Arif Shekh, Nusrath Tabassum, Md Abdus Samad Kamal, and Kou Yamada. Include a compact author line if appropriate, clearly distinguishing the presenter from the paper's coauthors. Preserve the manuscript's affiliation assignments if listing all author affiliations. Do not automatically label every coauthor as a thesis supervisor.

Use student ID, defence date, degree details, or university logos only when supplied or verified. Do not invent missing information. Keep the title slide clean and readable.

### Slide 2 — Global situation and problem statement

Section label: **Introduction**

Explain why pedestrian crossing prediction matters for road safety. Use Figure 1 and the Introduction's cited statistics. The manuscript reports approximately 1.16 million annual road traffic deaths, road traffic injuries as the leading cause of death among ages 5–29, and pedestrians accounting for 23% of global road traffic deaths in 2021, approximately 274,000 fatalities.

Keep the original years and source contexts. Do not combine percentages and totals from different reporting years to calculate a new statistic. Do not label all figures as measurements from the presentation year. If updating any statistic, verify an official source and record its date and citation.

On this same slide, state the specific research problem clearly: **prediction needs observations from before crossing begins, but observation-window construction can introduce crossing frames or different temporal positions for the two classes, affecting reported performance**.

This gives the audience both the world situation and an explicit problem statement without changing the required positions of slides 3–5.

### Slide 3 — Research questions

Section label: **Introduction**

Present the three research questions from Section 1 in concise wording:

- RQ1: Are the generated observation windows temporally valid against frame-level crossing onset across PIE, JAAD, and IDD-PeD?
- RQ2: After removing crossing-frame contamination, does class-dependent temporal sampling remain, and how does phase matching affect performance and the contribution of ego-vehicle speed?
- RQ3: Do relative performance differences among BiLSTM, GRU, vanilla RNN, and Transformer models remain consistent across temporal sampling protocols?

Preserve all three questions. Do not replace them with generic project objectives.

### Slide 4 — Research contributions

Section label: **Introduction**

Present the four actual contributions from Section 1:

- A frame-level temporal-validity audit on PIE, JAAD, and IDD-PeD.
- Event anchoring and a training-derived phase-matched control on PIE.
- Bounding-box-only versus bounding-box-plus-speed comparisons under both protocols.
- Controlled comparisons of four temporal model families, with repeated runs and statistical evaluation.

Describe the contribution as auditing sample construction and testing sensitivity to the sampling protocol. Event-relative prediction itself is established prior work. Do not claim that this study invented it, introduced a new state-of-the-art architecture, or proved that ego speed is universally uninformative.

### Slide 5 — Presentation roadmap from the final Introduction paragraph

Section label: **Introduction**

Use the **last active paragraph of Section 1**, which describes how the paper is organized. Convert it into a brief presentation roadmap: Related Work; Materials and Methods; Experimental Settings; Results; Discussion and Limitations; Conclusions.

Do not replace this paragraph with the final Related Work paragraph, the contribution list, or the conclusion. Slides 2–5 form the four-slide Introduction, following the title slide.

### Slides 6–8 — Related Work

Section label on all three: **Related Work**

Use three focused slides, with the four Related Work subsections covered across them.

**Slide 6: Benchmark semantics and temporal evaluation.** Explain the distinction between latent intention and future observable crossing action. Cover JAAD, PIE, the established pre-event benchmark, and the remaining need to verify generated frames against crossing annotations. Use Section 2.1 and its actual references.

**Slide 7: Input representations and temporal models.** Use Sections 2.2–2.3. Summarize representative rich-input approaches and restricted-input approaches, including bounding boxes and ego speed. Use a compact editable literature comparison where helpful. Explain that scores across papers also reflect differences in inputs, preprocessing, tuning, and training. Cite actual studies such as IntFormer, PedCMT, the box-only Transformer study, and representative multimodal methods as appropriate. Do not imply that these published systems were all reimplemented here.

**Slide 8: Evaluation reliability and research gap.** Use Section 2.4 and the final active Related Work paragraph. Cover class imbalance, multiple random seeds, correlated windows from the same pedestrian, model-selection separation, and external validity. End with the precise gap addressed by this study: checking direct crossing-frame contamination and measuring how class-dependent sampling phase affects input and architecture comparisons.

Keep the literature discussion readable. Use a few well-chosen studies and concise author–year citations rather than reproducing the bibliography. If a fourth Related Work slide is essential, recover space elsewhere while keeping the entire deck at 25 slides or fewer and preserving slides 1–5 and 9–13 in their required relative order.

### Slide 9 — Materials and Methods: complete pipeline

Section label: **Methods**

Use the **entire Figure 2**, figures/fig2_method.png. Do not show only the upper half, the sequence encoder alone, or a cropped subset.

Retain the complete sequence: annotated pedestrian track; pre-event observation window; bounding boxes and ego speed; input construction; training-derived standardization; temporal model; crossing probability and binary decision.

Preserve all four model families and the figure's “one architecture per run” meaning. The four families are compared separately. A five-seed ensemble averages runs within a family; it is not an ensemble combining all four architectures.

The full figure should dominate the slide. Keep surrounding text short. Crop only blank margins. If improving label readability, preserve every component and relationship.

### Slide 10 — Section 3.1: datasets and partitioning process

Section label: **Methods 3.1**

Present the process first, before the dataset figure:

- PIE is the primary controlled benchmark.
- Exclude pedestrians with crossing label −1.
- Use the observed crossing outcome as the target, rather than intention_prob.
- Partition recording sets before generating observation windows.
- Training: sets 01, 02, and 04. Validation: sets 05 and 06. Testing: set 03.
- Keep all windows from a pedestrian in one partition and retain the same PIE partition across experiments.

Use a clear editable process or split diagram. Briefly identify JAAD as an external temporal audit dataset and IDD-PeD as an audit and exploratory external-evaluation dataset. Do not describe a random split of individual windows.

### Slide 11 — Section 3.1: full dataset figure

Section label: **Methods 3.1**

Use the **entire Figure 3**, figures/fig7_scenes.png, with the PIE, JAAD, and IDD-PeD panels.

Explain the dataset roles and annotation differences with only a few short labels. JAAD lacks the synchronized ego-speed channel required for this study's five-dimensional input, so it is not part of the four-family full-input prediction comparison.

The figure's orange boxes indicate the dataset's eventual crossing outcome and grey boxes indicate non-crossing. These colours are **annotation outcomes, not model predictions**. Preserve the blurred faces and the original panel labels.

### Slide 12 — Section 3.2: temporal extraction and control process

Section label: **Methods 3.2**

Present the process before the sampling figure. Explain the three distinct procedures: historical track-end extraction for auditing, event-anchored extraction, and event anchoring with phase-matched non-crossing windows.

Show how frames are ordered, contiguous pre-event segments are retained, complete 16-frame windows are sampled, and every observed frame is checked against the crossing annotation. A window is contaminated if at least one input frame is already annotated as crossing.

Explain the phase control: keep crossing windows in their original event-relative positions; estimate the observation-to-track-end distance distribution using **positive training windows only**; resample non-crossing windows using that fixed distribution; retain complete consecutive windows within feasible track ranges; exclude tracks without eligible windows; retrain the models while retaining recording-set assignments.

Mention that the observation-to-track-end distance is a sampling diagnostic and **is not a model input**. In notes, explain the IDD-PeD adjusted event reference as the earlier of the supplied crossing point and the first annotated crossing frame. Do not imply that training used the validation or test distance distribution.

### Slide 13 — Section 3.2: complete sampling figure

Section label: **Methods 3.2**

Use the **entire Figure 4**, figures/fig3_anchors.pdf. Show both panels, crossing and non-crossing tracks, event markers, observation windows, and timing relationships. Do not use only one panel.

Explain the contrast between historical extraction and event anchoring with phase matching. The 16-frame observation window ends 30–60 frames before the event, approximately 1–2 seconds at 30 fps. Distinguish this prediction horizon from the observation-window length.

Keep the figure intact and readable. Do not substitute a simplified drawing that omits a class, a panel, or a sampling rule.

### Slide 14 — Section 3.3: input representation and preprocessing

Section label: **Methods 3.3**

Show the frame-level input [x1, y1, x2, y2, v_ego], with bounding-box coordinates in the original image coordinate system and speed aligned by frame identifier.

Explain the two conditions: **16 × 5** bounding-box-plus-speed sequences and **16 × 4** bounding-box-only sequences. Show training-derived channel standardization using the same statistics for validation and testing. Figure 2 identifies this as z-score standardization.

Explain that the speed ablation changes the input channel while retaining the protocol, recording-set partitions, family configuration, random seeds, and evaluation procedure. Appearance images, pose, and scene semantics are not prediction-model inputs in these experiments.

### Slide 15 — Sections 3.4–3.5: temporal models and controlled evaluation

Section label: **Methods 3.4–3.5**

Use a concise editable comparison of BiLSTM, bidirectional GRU, bidirectional vanilla RNN, and Transformer. Explain gated recurrence, ungated recurrence, and self-attention in plain language.

All families receive the same type of observation sequence and produce one crossing probability. Emphasize shared data and evaluation procedures, while noting that model capacities and validation-selected configurations are not identical. Do not describe the hyperparameters, parameter counts, or search budgets as equal.

Summarize the training/validation/test roles and the four reported metrics: ROC-AUC, PR-AUC, F1, and accuracy. Explain that thresholds are selected using validation predictions and that accuracy is descriptive. Put detailed evaluation mechanics in notes and on the Experimental Settings slide.

If extra method explanation is necessary, add or split a slide only after checking the total slide budget. Retain the two process-before-figure pairs and the full pipeline slide.

### Slide 16 — Experimental settings

Section label: **Experimental Settings**

Use exactly one main slide for Section 4. Present a concise, readable experimental setup with the essential settings:

- CPU execution on an Apple M4 MacBook Air.
- 16-frame windows, stride 8, and a 30–60-frame prediction horizon.
- Event-anchored PIE: 4,906 windows, split 2,178 / 634 / 2,094.
- Phase-matched PIE: 4,520 windows, split 2,084 / 563 / 1,873.
- Adam, binary cross-entropy, batch size 32, maximum 100 epochs, and early stopping after 15 epochs without validation-AUC improvement.
- Five seeds: 42, 0, 1, 2, and 3.
- Validation-selected checkpoints and F1-maximizing thresholds.
- 10,000 pedestrian-clustered bootstrap replicates and Holm–Bonferroni correction at alpha = 0.05.

Use compact table rows or clearly grouped text. Put software versions, family-specific hyperparameters, learning-rate scheduling, positive-class weights, and search counts in speaker notes rather than shrinking the slide text. Retain the manuscript's actual settings and version strings when reporting them.

Explain in notes that statistical contrasts use probabilities averaged across seeds, whereas result tables report means across seed runs. Shared test pedestrians use paired bootstrap resamples. The two sampling protocols are resampled independently because their eligible pedestrian populations differ.

### Slide 17 — Results: temporal-validity audit

Section label: **Results**

Use the table labelled tab:temporal-audit in Section 5. Show the original versus corrected observation-window audit across all three datasets.

Preserve the key contamination rates: PIE historical extraction 67.9% of positives; JAAD naive extraction 93.0%; IDD-PeD track-end extraction 81.3%. Corrected PIE and JAAD windows show 0.0% observed contamination. On IDD-PeD, the supplied crossing_point still leaves 29.6% of positives contaminated; the earlier event/onset reference gives 0.0%.

Keep denominators explicit. Do not describe these percentages as percentages of every dataset's full window population. These are results for the **audited extraction procedures**, not a claim that all published uses of these datasets are contaminated.

### Slide 18 — Results: event-anchored model comparison

Section label: **Results**

Use the table labelled tab:model-results. Present all four families in a readable editable table or faithful chart, with five-seed means and standard deviations where space permits.

Preserve the main findings: vanilla RNN has the highest mean ROC-AUC, F1, and accuracy; Transformer has the highest mean PR-AUC. Do not identify one family as the best across every metric.

Key source values include vanilla RNN ROC-AUC 0.9481 ± 0.0058 and F1 0.8487 ± 0.0154, and Transformer PR-AUC 0.8964 ± 0.0188. Seven of 18 architecture–metric contrasts survive Holm correction. The manuscript reports no statistically supported difference between Transformer and vanilla RNN for the tested AUC, PR-AUC, and F1 contrasts.

### Slide 19 — Results: residual timing difference and phase control

Section label: **Results**

Use Figure 5, figures/fig4_phase_separation.png, to show both protocols.

Explain that event anchoring removes crossing frames but leaves class-dependent temporal position. Observation-to-track-end distance alone has AUC 1.0000 under event anchoring. After phase matching its diagnostic AUC is 0.7919 over the full dataset and 0.8241 on the test split.

State that phase matching **reduces the timing difference without eliminating it**. This diagnostic AUC is not a neural crossing-prediction score and the diagnostic distance is not supplied to the prediction models.

### Slide 20 — Results: model performance after phase matching

Section label: **Results**

Use the table labelled tab:phase-control and Figure 6, figures/fig5_curves.pdf. Explain that all four full-input models have lower mean performance on every reported metric after phase matching. The corrected architecture comparisons change from 7 of 18 supported contrasts to 0 of 18.

Choose a layout that makes the evidence readable. Use the full operating-characteristic figure if all panel titles, axes, and legends remain legible. Otherwise show complete, clearly identified ROC panels on the slide and place the full ROC/PR figure and detailed table in notes or an accompanying source document. This option applies only to this results figure; the required method figures on slides 9, 11, and 13 must remain complete.

Do not relabel Figure 6's five-seed probability-ensemble curve areas as the per-seed mean values in the tables. Do not interpret a lack of supported contrasts as proof that the architectures have equal performance.

### Slide 21 — Results: ego-vehicle speed ablation

Section label: **Results**

Use the table labelled tab:speed-phase. Make the box-only versus box-plus-speed comparison clear under both protocols. Define Delta as box-plus-speed minus box-only.

A compact four-row PR-AUC comparison can show the mean gains before and after phase matching: BiLSTM +0.2189 / −0.0206; vanilla RNN +0.1527 / −0.0188; GRU +0.1217 / +0.0049; Transformer +0.0565 / −0.0006. Use the manuscript's deltas, calculated from unrounded values, rather than recalculating them from rounded displayed means.

The statistical summary is 10 of 12 supported input contrasts under event anchoring and 0 of 12 after phase matching, across ROC-AUC, PR-AUC, and F1. Distinguish these ensemble-based inferential comparisons from the displayed descriptive mean deltas.

Use the conclusion: **the measured contribution of ego-vehicle speed is sensitive to temporal sampling**. Do not claim that speed is useless, that removing it reliably improves prediction, or that a causal mechanism has been isolated.

### Slide 22 — Results: qualitative detector-to-prediction demonstration

Section label: **Results**

Use Figure 7, figures/fig6_demo.png. Briefly explain the YOLO detector, ByteTrack association, tracked bounding boxes plus recorded speed, and frozen five-seed ensemble.

Show the contrast between stationary-vehicle scenes and the scene at 14 km/h, using the manuscript's panel labels. Predictions are associated with vehicle speed in the observed demonstration.

Label this clearly as **qualitative evaluation**. It is not the annotated-box quantitative test, a separate benchmark score, a validated safety system, or a deployment-performance claim. Do not describe the observed association as causation.

### Slide 23 — Discussion

Section label: **Discussion**

Interpret the evidence and connect it to the research questions. Explain that checking frame-level temporal validity and controlling class-dependent sampling are separate steps.

Summarize the supported conclusions: the tested extractions can contain crossing frames; event-marker semantics require dataset-specific checks; residual sampling phase affects the measured benefit of speed and the statistical evidence for architecture differences.

State the practical implication for research evaluation: report observation-window construction and audit its temporal validity alongside modality and model comparisons. Do not turn the discussion into an unsupported ranking of models or a claim of universal generalization.

### Slide 24 — Limitations and future work

Section label: **Limitations**

Use Section 6.1. Clearly distinguish limitations from proposed future work.

Limitations include a controlled phase-matched comparison confined to PIE; partial rather than complete timing alignment; changes in eligible populations and potentially pedestrian distance/box scale; restricted inputs; an observed crossing-outcome target rather than latent intention; and exploratory IDD-PeD transfer without the main PIE statistical analysis.

Future work should follow the manuscript: repeat the phase-matched comparison on an external dataset with synchronized ego motion, examine domain adaptation, and extend the audit and sampling control to richer input modalities.

Do not claim successful external transfer or invent external-test metrics.

### Slide 25 — Conclusions and closing

Section label: **Conclusions**

Use Section 7 to provide concise, evidence-bound conclusions: audit generated windows against frame-level crossing onset; check remaining class-dependent sampling phase; interpret input-feature gains and model rankings together with benchmark construction.

End with a brief closing or “Questions” line on this slide. Do not add an extra thank-you or Q&A slide that makes the deck exceed 25 slides. Do not introduce new results or promises in the conclusion.

## Styling and presentation rules

- Use a 16:9 widescreen format and a white background throughout.
- Use a restrained academic palette: dark text, one consistent navy or blue accent, and light grey rules where useful. Preserve scientific colours in source figures.
- Use one readable font family consistently, such as Aptos, Arial, or an equivalent available font. Aim for 30–36 pt slide titles and 22–26 pt body text. Use figure and table labels large enough to read during projection. Keep short source citations and section labels around 12–14 pt.
- Give each slide one clear purpose and a descriptive title. Prefer concise topic titles for method and setup slides, and carefully supported takeaway titles for result slides.
- Put a **short section label in the same upper or lower corner on every slide**, including the title and closing slides. Use the labels in the plan. Add a discreet slide number consistently.
- Keep content on a flat, uncluttered canvas with generous whitespace. Avoid dark themes, decorative gradients, dashboard cards, excessive icons, stock-photo decoration, and flashy transitions.
- Do not paste manuscript paragraphs onto slides. Summarize them faithfully and use notes for detailed explanation.
- Use past tense for completed sampling, training, and evaluation procedures. Use present tense for general facts, definitions, and what a figure shows. Keep tense consistent within each explanation.
- Avoid repeated “we,” inflated novelty claims, promotional wording, and unexplained abbreviations.
- Keep text, tables, and equations editable. Use original figures at high quality with preserved proportions. For PDF figures, use vector insertion where supported or a high-resolution rendering.
- Never crop away evidence or stretch an image. Do not recreate empirical curves, bars, or confidence intervals from guessed data.
- Keep exact metrics, denominators, years, units, input dimensions, thresholds, and uncertainty types consistent with the source.
- Cite literature and external statistics briefly on the relevant slide and provide fuller reference details in notes. Use references.bib. Do not use the ZIP filename as the study title or invent numbered reference assignments.
- A standalone reference slide is optional only if the total remains at 25 or fewer and all required content remains covered. References can instead be documented in speaker notes and an accompanying reference file.
- Put working comments, layout checks, and development details in the plan or review file, never in the audience-facing slides or speaker notes.

## Final quality check

Check **every slide**, then recheck the complete sequence:

1. The first five slides have the required order and slides 2–5 cover the Introduction.
2. There are three or four Related Work slides.
3. The method overview uses the full pipeline. Both Section 3.1 and Section 3.2 use process first, then the correct full figure.
4. Input representation, model comparison, training/evaluation, one experimental-setting slide, results, discussion, limitations, and conclusions are covered.
5. The current manuscript title, presenter information, section labels, and figure numbering are correct.
6. Every number and claim matches the active manuscript or a documented verified source. No old commented-out wording has been used.
7. Mean-over-seeds results, seed variability, probability-ensemble metrics, bootstrap confidence intervals, and Holm-adjusted comparisons remain distinct.
8. The presentation does not equate non-significance with equivalence, claim complete removal of sampling bias, or treat exploratory/qualitative observations as quantitative validation.
9. Every slide is readable at normal presentation size, with no overlap, clipping, missing objects, illegible legends, or accidental figure cropping.
10. The final count is at most 25, including closing and any backup/reference slides. The PPTX and PDF agree.

## Deliverables

Commit the finished work under presentation/:

- Thesis_Defence_Arif_Shekh.pptx — complete editable main deck.
- Thesis_Defence_Arif_Shekh.pdf — matching presentation export.
- presentation_plan.md — the plan followed, updated to match the final deck.
- review_notes.md — a concise record of source checks, final slide count, and any unresolved issue requiring Arif's input.
- Any necessary source/reference material or build files needed to update the deck.

Include useful speaker notes in the PPTX. Preserve the supplied manuscript files. Do not publish the presentation elsewhere unless Arif requests it.

The work is complete only when the full deck is built, checked slide by slide, corrected, and delivered with matching exports.

