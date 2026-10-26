# GALE-CAST: Model History, Training, Scores, and Evidence

Prepared 26 October 2026. All times identified as PHT use Philippine time (UTC+08:00).

This Markdown file explains the available original model-development records in basic English. It includes the earlier models, the original W1 training, architecture, settings, model comparisons, score calculations, recovered epoch tables and source files. Missing records are labelled. No new training, scoring, database work or project-file edits were performed to create it.

## 1. What “complete” means for this document

All requested topics are discussed. That does **not** mean every original experiment record has been recovered. A missing seed cannot be recovered from a final score. A missing epoch loss cannot be reconstructed from a saved model. A later experiment cannot supply the missing log of an earlier experiment.

The main conclusion is clear: **the current local saved model is W1, trained on 15 September 2026. The final W1+X1 score and cutoff were selected afterward, on 17 September.** The exact artifact identity and those original records are available. The whole-network training seed, full original 49-epoch numeric history, and a complete controlled architecture/hyperparameter search remain unavailable in the files searched.

## 2. Results of the focused search for the missing records

| Requested missing item | What was found | What is still missing |
|---|---|---|
| Whole-network training seed | Seed **42** is explicitly set for noise added to copied event-positive training inputs | No explicit original TensorFlow/Keras initialization seed, shuffle seed, or matched multi-seed W1 record was found |
| Complete path to W1 | All 36 located notebook versions, September v11–v14 records, seven staged retrains, and the original X1/cutoff steps; additional September bug-fix explanations were located | A guaranteed record of every trial ever attempted |
| Architecture selection | Exact saved layers, dimensions and parameter count; version changes leading to the shared model | A controlled comparison proving why 64/32 units, attention and 32 days were best |
| Hyperparameter tuning | Actual recorded weighting, focal-loss, feature, split and threshold experiments | An isolated ablation and repeat-seed log for every setting |
| Independent benchmark | Original saved candidate comparisons and original target checks | A newly located, genuinely independent W1 test benchmark; none was found in this follow-up |
| W1 epoch history | Ten complete numbered summaries: **epochs 13–22**; statements confirming best epoch **37** and stopping at **49** | Numeric rows for **epochs 1–12 and 23–49**, including the final epoch’s numeric summary |
| Earlier models | Located historical models and all available notebook versions | Proof that no other unrecorded or deleted attempts existed |

The supplied review refers to later comparisons with persistence and climatology. Those are separate evaluations, outside the original-training scope you previously requested. They do not prove that the original W1 training had an untouched independent test, and they do not fill its missing seed or epoch records. This document keeps the original model-to-model comparisons and does not re-label later work as original training evidence.

### Files and records checked again

- The exact original W1 trainer and its recorded seed/randomness settings.
- The original September session and its surviving training-log excerpts.
- Other related local Claude records for the original training-log name and completion markers.
- Tracked file paths across local git history.
- Member names inside the project ZIP backup, without extracting or changing the archive.

The backup contains training histories for later W1-derived experiments with seeds 11, 22 and 33, and for the later original-split improvement experiment. Those are real records, but they belong to other trained artifacts. They must not be described as W1’s original seed or epoch history.

Search details: [MISSING_RECORDS_FOLLOWUP_SEARCH.json](downloads/MISSING_RECORDS_FOLLOWUP_SEARCH.json). Additional original-history references: [ADDITIONAL_ORIGINAL_HISTORY_FINDINGS.json](downloads/ADDITIONAL_ORIGINAL_HISTORY_FINDINGS.json).

## 3. Additional original history recovered in this follow-up

These findings extend the explanation of how the earlier model reached W1. They are from the original September development session, not from later benchmark results. Historical statements describe the model that existed at their date; the same model filename was reused over time, so a September 7 statement must not automatically be attributed to the September 15 W1 weights.

### September 7–8: why fixing the displayed score was not enough

The original discussion found that the earlier label-building code took the **maximum event label inside the input window**. In basic English, if an event appeared anywhere in the last 32 days, many overlapping windows could all be counted as positive. That question is different from “will the event happen on the next target day?”

It also found that some windows could cross from one station’s rows into another station’s rows. A weather sequence should belong to one station; joining two different stations inside one sequence changes the meaning of its history.

A scoring-script correction changes how an existing prediction is checked. It does not change what a previously trained network learned. The September 8 discussion therefore explicitly said a **training-label fix and a retrain** were needed. This helps explain why another saved model was built instead of only updating the displayed confusion matrix.

Sources: original session lines **17311**, **18233** and **20834**. The later W1 trainer uses the corrected next-day label. These earlier findings are not claims that W1 itself still used the older window-maximum target.

### September 8: v11 was a separate saved retrain

The original tool output confirms that the v11 run reached **epoch 50** and wrote versioned v11 model, scaler and threshold files. This is direct evidence of another recorded training attempt before W1. Its later headline use was limited because its early-stopping and reporting dates were not sufficiently separated, as explained in the original threshold document. Source: original session line **22575**.

### September 9: window rules affected both tuning counts and results

The original records describe correcting how the tuning slice was turned into input windows. A slice can contain many raw rows, but its early rows may be used only to build the first 32-day history. They are not automatically separate scored cases. Missing that distinction changes the number of available tuning events.

The same records describe a v13 retrain that changed date-split constants. Its original summary reports stopping at **epoch 43**, with best epoch **31** and validation gale loss **0.0132**. Those numbers belong to **v13**, not W1. The dates and window rules also changed, so a score difference cannot be attributed only to neural layer quality. Sources: original session lines **24940** and **25218**.

### September 15–17: seven retrains, then scoring choices

The original September 17 summary explicitly counts **seven newly trained variants** in the staged experiment: W1, W2, W3, F1, F2, X1f and X2f. It reports **24 scored configurations** across that stage’s prompts, including raw versus X1 scores and different threshold rules. Source: original session line **28224**.

This count closes part of the missing history for that specific experiment. It is not a count of every model ever trained in the project. The phrase “24 configurations” includes scoring choices that reuse an existing model; it does not mean 24 new networks were trained.

Trying many candidates can help find a better recorded result, but choosing the best result from those attempts can also make the winner look better than it would on new data. The original summary itself acknowledged this selection effect. Therefore the result should be called an original development/selection result, not proof of an untouched independent benchmark.

## 4. How to read the main documentation and appendices

The following main record contains the complete available explanation and all recovered notebook epoch tables. Read the summary and glossary first; then use the model-history, W1-epoch, original-comparison, architecture and score sections. The long notebook epoch tables are evidence appendices: you do not need to read all rows to understand how W1 was chosen.

## Main record: coverage of all requested topics

**This report explains every requested topic in basic English, but the original records do not contain every requested detail.** Missing records are labelled below. An explanation of a missing record is not a replacement for that record.

| Your question | What is covered | Evidence status |
|---|---|---|
| Seed training record | The original W1 trainer uses seed 42 for added-example noise; no whole-network training seed or repeat-seed W1 run record was found | Partial original record |
| Confusion matrix, accuracy, precision and recall | Explicit 2×2 matrix, definitions, count-by-count calculations and original saved scores | Covered for the final binary W1+X1 score |
| How the current model was reached | Every available notebook version, original September model variants, X1 and cutoff selection | Covered for located history; not proof that no other trials ever existed |
| How the score was obtained | Input windows → saved model → probabilities → X1 → cutoff → counts → metrics; training and post-training scores kept separate | Covered for classification; the full origin of every weather-score row is not established by the threshold document alone |
| How the architecture was reached | Event-only branches → weather head → 32-day pipeline → retained W1 architecture; explains each component | Recorded structure covered; a controlled search proving each layer size was best was not found |
| Tuning choices | Date splits, early stopping, losses, class-weight trials, extra-feature trials and threshold rules | Covered for the recorded original trials |
| Parameters | Layer sizes, 40,872 learned parameters, loss settings, batch size, epochs, recency base and sampling settings | Covered for the original W1 script; unspecified random initialization remains unspecified |
| Benchmarking | Original model-to-model comparison and original target checks | Covered within your requested original-development scope |
| Improvement per epoch | All recovered notebook rows plus W1 epochs 13–22, including increases in error | Partial: the complete W1 49-epoch numeric history was not found |
| All models before W1 | All 36 located notebooks and located September variants, with file references and repeated-output warnings | Located history covered; a complete record of every possible unrecorded trial cannot be claimed |

## Read this first

**The current local model is W1.** Its training was launched on **15 September 2026 at 3:17:28.961 PM PHT**. Its saved file is dated **4:16:46.778 PM PHT** that day. It stopped at **epoch 49**, with **epoch 37** recorded as the best. The familiar final score was selected on **17 September**, after the same model’s probabilities were averaged across stations and a cutoff of **0.601** was chosen.

The recorded development path is: earlier event-only notebooks → a model with event and weather outputs → changes to data, targets, scaling and loss settings → September retrains and comparisons → W1 → cross-station probability averaging (X1) → the final cutoff. The older notebook files did not directly produce the current W1 weights; the original September `_train_w3.py` did.

**What an epoch means:** one pass through the training examples. During that pass, training adjusts the model’s internal numbers, called weights. It does not normally rewrite the code or redesign the model. A code fix, a new input or a new loss setting is a change **between runs**. This report records epoch learning and between-run edits separately.

**Important evidence limit:** I extracted **820 saved notebook epoch-summary rows**, but many are repeated across files. They form **10 distinct extracted metric sequences**, not proof of 820 independent epochs across independent retrains. For the actual W1 run, I recovered **10 numbered epoch summaries, epochs 13–22**, plus the original completion and best-epoch statements. The missing W1 epoch scores are left missing.

## Simple guide to the terms

| Term | Basic meaning |
|---|---|
| Architecture | The model’s layers and how they connect |
| Parameter / weight | An internal number learned during training; W1 has 40,872 |
| Hyperparameter | A setting chosen before a run, such as batch size, loss weight or number of days |
| Training loss | The error number the optimizer tries to reduce on training examples |
| Validation or TUNE loss | Error on the separate data used to watch learning and choose settings; lower is better |
| Early stopping | Stop after the watched error fails to improve for a chosen number of epochs |
| Restore best weights | Keep the model from the best watched epoch, rather than the final epoch |
| Classification | Predict whether the study event happens |
| Regression | Predict a number, such as wind speed or pressure |
| TP / FP / FN / TN | Correct alert / false alert / missed event / correct non-alert |
| Precision | Of the alerts made, how many were correct |
| Recall | Of the actual study events, how many were caught |
| F1 score | One score combining precision and recall |
| PR-AUC | How well probabilities rank events across different cutoffs; higher is better |
| MAE / RMSE | Numerical forecast errors; lower is better; RMSE gives large errors more weight |
| Same saved output | The recorded epoch numbers match exactly; this does not establish that the edited code was rerun |

### Seed record: what 42 does and does not mean

A seed is a starting number for a random-number generator. Reusing it can repeat the random choices made by that generator. It does not automatically control every random choice in a training program.

In the original `_train_w3.py`, **line 843** contains `rng_os = np.random.default_rng(42)`. That generator makes small Gaussian noise with mean 0 and standard deviation **0.01** for copied event-positive input sequences. Both normal and anomaly inputs receive that noise, stored as float32. The copied examples keep their target labels. This gives the model extra, slightly varied positive examples to learn from.

The original script does **not** set a TensorFlow/Keras whole-training seed, and it does not explicitly set a training shuffle seed. The model’s starting weights and other training randomness are therefore not pinned by the number 42 above. No W1 multi-seed comparison was located. The correct statement is: **“The extra-example noise uses seed 42; the complete original W1 training seed record is missing.”** That is why the saved weights can be identified by their file hash, but a byte-for-byte retrain cannot be promised.

The original scoring script also has bootstrap routines with seed 42. A bootstrap seed repeats statistical resampling after scoring; it is not the seed that trained the neural network.

### What the architecture components do, and why the history does not prove an optimum

An **LSTM** reads a sequence while learning which earlier information to keep. The normal branch reads a larger weather history. The anomaly branch reads four changing-weather signals. **Recency weighting** gives more emphasis to recent days; the original base is **0.9**. **Attention** learns how strongly to use each position in that history. **Dense layers** combine the information. **Dropout 0.2** randomly leaves out a fifth of the merged values during training to discourage dependence on only a few connections. A **sigmoid** maps an output into the 0–1 range.

These are basic explanations of what the implemented parts do. The saved history shows the two event branches were already present in the early notebooks; v3.0 added weather outputs; v5.0 moved the shared window to 32 days; W1 retained that structure while changing the training recipe. I did not find a controlled original search comparing every layer size, attention versus no attention, or every window length on identical cases. It would be unsupported to claim that 64/32 LSTM units or 32 days were proven optimal.

### How the 40,872 learned parameters are counted

| Layer | Learned numbers |
|---|---:|
| Normal LSTM: 32 inputs, 64 units | 24,832 |
| Normal Dense: 64 → 32 | 2,080 |
| First anomaly LSTM: 4 inputs, 32 units | 4,736 |
| Attention Dense: 32 → 1 | 33 |
| Second anomaly LSTM: 32 inputs, 32 units | 8,320 |
| Anomaly Dense: 32 → 16 | 528 |
| Event head: 48 → 1 | 49 |
| Weather head: 48 → 6 | 294 |
| **Total** | **40,872** |

An LSTM with f inputs and u units has 4×u×(f+u+1) learned numbers in this saved model. A Dense layer with f inputs and u outputs has f×u+u. Attention softmax, multiplication, concatenation and dropout add no learned numbers here. These counts explain the saved architecture; they are not new training results.

The original regression example weight is `1 + scaled wind_speed`; examples in the top 10% of scaled rainfall receive another ×2. The event-head weights use the recorded class-balancing scheme and W1’s negative-class ×3 setting. Those are the configured training choices. Their presence in code does not, on its own, prove that each choice caused a score improvement.

### How one saved forecast becomes the final score

First, the scorer constructs each eligible station’s 32-day input window and obtains the study label from its next-day wind/pressure rule. It passes the two input arrays into the saved W1 network. The event head returns a probability. X1 averages the probabilities across available scored stations for the same date. The selected decision cutoff turns that score into an alert or a non-alert. The scorer then compares that decision with the saved study label for each case, counts correct and incorrect decisions, and calculates the metrics. It does not update the network weights while calculating those scores.

For the locked original binary result, rows are the actual label and columns are the predicted decision:

| Actual / predicted | No alert | Alert | Total |
|---|---:|---:|---:|
| No study event | **3,386 TN** | **9 FP** | 3,395 |
| Study event | **4 FN** | **24 TP** | 28 |
| Total | 3,390 | 33 | **3,423** |

**Accuracy:** 3,410 correct decisions ÷ 3,423 cases = **99.6202%**, displayed as 99.62%. **Precision:** 24 correct alerts ÷ 33 alerts = **72.7273%**, displayed as 72.73%. **Recall:** 24 caught events ÷ 28 actual events = **85.7143%**, displayed as 85.71%. **F1:** 48 ÷ (48+9+4) = **78.6885%**, displayed as 78.69%. PR-AUC is **0.8302** from the original ranked probability scores; it cannot be calculated from this one matrix alone.

In basic English: the model made 33 alerts. Twenty-four matched the study event label and nine did not. Four of the 28 labelled events were missed. The event label is the project’s wind-or-pressure-drop rule; a pressure-triggered label is not proof of observed gale-force wind. The high accuracy is helped by the large number of non-event cases, so precision and recall are needed to understand alert behaviour.

The same saved JSON also contains a 3×3 High/Moderate/Low matrix. That matrix uses a different decision setup. It must not be substituted for this binary matrix to reproduce the headline metrics. The original binary counts above are the counts behind the locked W1+X1 headline.

### Original benchmarking: what was compared and what was achieved

Here, benchmarking means comparing the original candidate models and checking the original targets. The full model table below shows their cutoff, alert counts and scores. W1+X1’s PR-AUC **0.8302171573350975** was above W2+X1 **0.7168353098477321**, W3+X1 **0.35647435946886047**, and X1f+X1 **0.7976339658670485** in those saved original comparisons. This is the recorded basis for keeping W1+X1. Date-partition trials v13/v14 use different cases, so their score differences cannot isolate architecture quality.

| Original target | Locked W1+X1 value | Result |
|---|---:|---|
| Precision at least 75% | 72.73% | Not met; short by 2.27 percentage points |
| Recall at least 85% | 85.71% | Met |
| F1 at least 0.75 | 0.7869 | Met |
| PR-AUC above 0.80 | 0.8302 | Met |

This explains the original benchmark results rather than claiming every target was achieved. It also does not turn the many previously inspected model trials into a new, untouched test. The exact original score files are downloadable with their source hashes.

## Main record A. Earlier models and changes, version by version

The following follows **notebook version order**. The exact execution date of every older notebook was not recovered. A file may include training, data preparation, validation, figures and dashboard code together. A change elsewhere in that file is not automatically a model-training change. The notebook links open the original evidence.

### The model families

| Family | What it did | Main change toward W1 |
|---|---|---|
| v1.0–v2.11 | Two-stream event classifier, generally with a 24-day window | Built the normal/anomaly branches, attention and event-training pipeline; tried different extra data sources |
| v3.0–v4.8 | Multi-output model | Added a weather head beside the event head; adjusted loss weights, targets and stopping settings |
| v5.0–v6.1 SUMMER | Later multi-output pipeline and separate direction experiments | Moved to 32-day windows and added target/scaler/feature corrections; direction-only trials were separate models |
| September v11–v14 | Additional split/recipe trials, distinct from notebook decimal names | Compared reported scores under different partitions and stopping choices |
| September W1/W2/W3, F1/F2, X1f/X2f | Original precision-targeting retrains | Compared class weighting, loss alpha and pressure features |
| W1+X1 at 0.601 | Selected current configuration | Used W1 weights, averaged station probabilities, then selected the alert cutoff |

### What each notebook changed

#### galecast_v1.0.ipynb

Starting point in the available notebook series: a two-branch model predicts the event label. It already uses recent weather, an LSTM in each branch, attention in the anomaly branch, and a 24-day window. The notebook contains seven saved epoch-summary rows.

Source: [galecast_v1.0.ipynb](#source-register). Saved epoch summaries: **7**. The extracted epoch sequence first appears in this file.

#### galecast_v2.0.ipynb

Changes the data-scaling and normalized-data handling around the classifier. The visible code fits scalers on training rows and carries station/date information with the transformed data. This is a data-pipeline change, not the later six-output weather model.

Source: [galecast_v2.0.ipynb](#source-register). Saved epoch summaries: **10**. The extracted epoch sequence first appears in this file.

#### galecast_v2.5.ipynb

Adds an extra gale-data table to the training rows, while keeping validation on real rows. The historical notebook ledger identifies the extra file used at this stage as a synthetic dataset. The input scalers are fitted using the real training rows. This changes the data given to the network.

Source: [galecast_v2.5.ipynb](#source-register). Saved epoch summaries: **25**. The extracted epoch sequence first appears in this file.

#### galecast_v2.6.ipynb

Adds the historical SMOTE data-generation stage. The ledger records generated SYN_ rows here. The neural training block is unchanged from v2.5, but the upstream data preparation changes. That can change training even when the model layers stay the same.

Source: [galecast_v2.6.ipynb](#source-register). Saved epoch summaries: **14**. The extracted epoch sequence first appears in this file.

#### galecast_v2.7.ipynb

Keeps the classifier training block. Much of the new code handles future feature rows and small random changes to those rows in the forecast pipeline. These changes should not be described as a newly designed neural architecture.

Source: [galecast_v2.7.ipynb](#source-register). Saved epoch summaries: **14**. The extracted epoch sequence first appears in this file.

#### galecast_v2.8.ipynb

Keeps the classifier training block. The differences include forecast-feature handling and preserving selected flag/season values. Its extracted saved epoch metrics are identical to v2.7, so the outputs do not establish a separate new training run.

Source: [galecast_v2.8.ipynb](#source-register). Saved epoch summaries: **14**. Its extracted epoch sequence is identical to **galecast_v2.7.ipynb**.

#### galecast_v2.9.ipynb

Keeps the classifier training block. The historical data ledger changes from generated SYN_ rows to supplementary station observations at this point. Other edits include wind units and output handling. The data source and the displayed result must be kept separate from the neural architecture.

Source: [galecast_v2.9.ipynb](#source-register). Saved epoch summaries: **18**. The extracted epoch sequence first appears in this file.

#### galecast_v2.10.ipynb

Keeps the classifier training block. Visible edits focus on average wind, wind-unit conversion and direction display. These explain a changed display, but do not prove the neural model improved.

Source: [galecast_v2.10.ipynb](#source-register). Saved epoch summaries: **10**. The extracted epoch sequence first appears in this file.

#### galecast_v2.11.ipynb

Keeps the classifier training block. Visible additions include recent-day weighting and forecast/display handling elsewhere in the notebook. Its saved training output is one of the distinct metric sequences in this collection; the code and outputs still need to be treated as separate evidence.

Source: [galecast_v2.11.ipynb](#source-register). Saved epoch summaries: **40**. The extracted epoch sequence first appears in this file.

#### galecast_v3.0.ipynb

Adds the multi-output model. It keeps the event-probability head and adds a six-value weather head for wind, humidity, direction sine/cosine, rainfall and pressure. A separate regression scaler and a weighted regression loss are added. The initial weather-loss weight is 0.3. Both old classifier and new multi-output code appear in this notebook.

Source: [galecast_v3.0.ipynb](#source-register). Saved epoch summaries: **34**. The extracted epoch sequence first appears in this file.

#### galecast_v3.1.ipynb

Changes the weather-loss weight from 0.3 to 0.5, giving weather error more influence in the combined training objective. It also contains many application changes. The saved extracted epoch metrics are identical to v3.0, so they cannot demonstrate the effect of this weight change.

Source: [galecast_v3.1.ipynb](#source-register). Saved epoch summaries: **34**. Its extracted epoch sequence is identical to **galecast_v3.0.ipynb**.

#### galecast_v3.2.ipynb

Removes the older classifier training block and keeps the multi-output block. Other edits include a Science Garden wind multiplier and matrix/display handling. The saved training output begins a metric sequence that is repeated in many later notebook files.

Source: [galecast_v3.2.ipynb](#source-register). Saved epoch summaries: **24**. The extracted epoch sequence first appears in this file.

#### galecast_v3.3.ipynb

Keeps the multi-output training block. Edits occur in scoring/data retrieval and forecast/display logic. There is no new neural training-block setting change established by the direct comparison with v3.2.

Source: [galecast_v3.3.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v4.0.ipynb

Changes several training settings together: regression-loss weight returns from 0.5 to 0.3; focal alpha becomes 0.80; early stopping uses a more targeted validation signal and patience 8. The code also includes target-scaling extremes, class boosts, positive-example handling and a window-maximum event label. Because several things change, one score difference could not isolate a single cause. Its saved epoch output remains the repeated older sequence.

Source: [galecast_v4.0.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v4.1.ipynb

Changes focal alpha from 0.80 back to 0.75. This changes how the classification loss is configured. The saved epoch output is unchanged, so the file does not show a newly observed epoch-by-epoch response to that edit.

Source: [galecast_v4.1.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v4.2.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v4.2.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v4.3.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v4.3.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v4.4.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v4.4.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v4.5.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v4.5.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v4.6.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v4.6.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v4.7.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v4.7.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v4.8.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v4.8.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.0-SUMMER.ipynb

Changes the shared model window to 32 days, changes the direction sine/cosine activations to sigmoid to match scaled targets, and adds extra regression weight to high-rainfall examples. Its saved epoch output is still identical to the repeated earlier sequence; the code change is real, but that output is not fresh proof of its effect.

Source: [galecast_v5.0-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.1-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.1-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.2-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.2-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.3-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.3-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.4-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.4-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.5-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.5-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.6-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.6-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.7-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.7-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.8-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.8-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.9-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.9-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.10-SUMMER.ipynb

The shared neural training block is unchanged from the previous version. The file contains changes outside that block, including prediction, scoring, calibration, figures or the application. Its shared-model epoch output is the same repeated sequence. A new notebook filename is not proof of a new neural training run or an accuracy gain.

Source: [galecast_v5.10-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v5.11-SUMMER.ipynb

Keeps the shared multi-output training block and adds a separate direction-only network. That direction network has its own lagged-direction inputs and a circular loss, so it must not be mistaken for the shared gale/weather network.

Source: [galecast_v5.11-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v6.0-SUMMER.ipynb

Expands the separate direction experiment with station-specific features/scalers, additional weather and cross-station signals, a larger direction LSTM, two dense layers, gradient clipping and a learning-rate schedule. The shared multi-output training block is retained. The direction experiments are separate from the W1 event-probability selection.

Source: [galecast_v6.0-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

#### galecast_v6.1-SUMMER.ipynb

Changes the shared pipeline to use the next row after the input window as the weather target, rather than the last input row; adds station-boundary protection, per-station scaling support and lagged cross-station direction features. It also contains further direction-only experiments and notes about changes that were tried and reversed. The repeated shared-model epoch output does not verify that all these edited settings were rerun.

Source: [galecast_v6.1-SUMMER.ipynb](#source-register). Saved epoch summaries: **24**. Its extracted epoch sequence is identical to **galecast_v3.2.ipynb**.

### What repeated outputs tell us

For example, v3.1 changes the weather-loss weight, but its saved epoch metrics match v3.0. More strongly, v3.2 through v6.1 share the same extracted shared-model metric sequence, even though later code changes targets and settings. These saved outputs cannot prove the training effect of each edit. They may have been carried forward when the notebook was copied or edited. I cannot turn those repeated outputs into a claim that each version improved.

The detailed settings found in each file, their changes from the preceding file, training-code hashes, notebook hashes and repeated-output groups are in [TRAINING_VERSION_CHANGES.json](downloads/TRAINING_VERSION_CHANGES.json). These are static code observations; they are not new training results.

## Main record B. Epoch-by-epoch progress recovered for the actual W1 run

These rows come from the original September session’s saved output of `train_w3_run.log`, at **session line 26945**. Only complete printed summaries with an identifiable epoch were included in this table. Error values are copied as printed. “Change” is the previous available epoch’s validation gale loss minus this epoch’s loss; positive means the watched error went down.

| Epoch | Training gale loss | Validation gale loss (watched) | Change | Validation total loss | What happened |
|---:|---:|---:|---:|---:|---|
| 13 | 0.0472 | 0.0115 | — | 0.0257 | First available complete row |
| 14 | 0.0455 | 0.0099 | 0.0016 | 0.0239 | Watched error went down |
| 15 | 0.044 | 0.0096 | 0.0003 | 0.0235 | Watched error went down |
| 16 | 0.0424 | 0.0096 | 0.0 | 0.024 | Watched error stayed the same |
| 17 | 0.0413 | 0.0101 | -0.0005 | 0.0242 | Watched error rose |
| 18 | 0.0393 | 0.0082 | 0.0019 | 0.0227 | Watched error went down |
| 19 | 0.0395 | 0.0129 | -0.0047 | 0.0273 | Watched error rose |
| 20 | 0.0385 | 0.0078 | 0.0051 | 0.0219 | Watched error went down |
| 21 | 0.0374 | 0.0102 | -0.0024 | 0.0242 | Watched error rose |
| 22 | 0.0361 | 0.0107 | -0.0005 | 0.0248 | Watched error rose |

In this available slice, epoch 20 has the lowest watched loss, **0.0078**. That is only the best in this slice, not the best of the whole run. The original completion discussion records **epoch 37** as the overall best. The saved excerpt does not provide epoch 37’s numeric loss. Training ended at epoch 49 after 12 epochs without a new best. Early stopping kept the best weights.

This shows why training progress is not a straight line: an epoch can lower training error while the watched validation error rises. The original script used the validation gale loss to decide stopping, not the final headline PR-AUC. A rise here is not evidence that the code was changed during that epoch.

For W1, **epochs 1–12 and 23–49 do not have full numeric rows in the recovered W1 extract**. The original session confirms epoch 1 began and epoch 49 was reached. The exact missing scores are not reconstructed or guessed. Other September session excerpts contain scores that cannot be safely assigned to a particular model or epoch; those remain marked “unassigned” in the full CSV.

Download every recovered metric column and source reference: [EPOCH_RECORDS.csv](downloads/EPOCH_RECORDS.csv) or [EPOCH_RECORDS.json](downloads/EPOCH_RECORDS.json). The CSV includes training loss, validation loss and other printed metrics when present; missing fields are blank.

## Main record C. The original September retrains: what was changed and what happened

These are original model-to-model experiments around the current model. They are separate from the decimal notebook versions. An attempt was useful only if its saved results supported it; the report keeps unsuccessful attempts too.

| Attempt | Setting changed / reason for trying it | Recorded result and decision | Original evidence |
|---|---|---|---|
| v11 | Earlier recipe; reported PR-AUC 0.8034 | Original threshold document says its early stopping watched the dates later reported as TEST; it was kept as a reference rather than the selected headline | validation_cm3_v11.json; THRESHOLD_CONFIG.md |
| v12 | Reference three-way date split with a separate tuning period | Raw PR-AUC 0.6916; used as the starting recipe for the later changes | validation_cm3_v12.json |
| v13 | Split B, 60/40 partition trial | PR-AUC 0.5184362130278758; different cases, so this does not isolate architecture quality | validation_cm3_v13.json |
| v14 | Split C, 65/35 with permissive windowing | PR-AUC 0.5232466253925905; again a different sample/protocol | validation_cm3_v14.json |
| W1 | Negative-class weight multiplier ×3, to reduce false alerts while retaining event ranking | Raw PR-AUC 0.7277791504254221; strongest W-weight candidate | variant_score_w3.json |
| W2 | Multiplier ×6 | Raw PR-AUC 0.6402825755001175; worse ranking than W1 | variant_score_w6.json |
| W3 | Multiplier ×10 | Raw PR-AUC 0.32418579787966995; much worse ranking than W1 | variant_score_w10.json |
| F1 | Focal-loss alpha 0.50 instead of 0.75; gamma stays 2; negative multiplier 1 | Raw PR-AUC 0.6417303783956378; not selected | variant_score_f1.json |
| F2 | Focal-loss alpha 0.25 instead of 0.75; gamma stays 2; negative multiplier 1 | Raw PR-AUC 0.6796913426073594; not selected | variant_score_f2.json |
| X1f | Add 2-, 3- and 5-day pressure-change features | Raw PR-AUC 0.752289067711023; a promising original candidate, but with X1 it remained below W1+X1 | variant_score_x1f.json |
| X2f | X1f plus a pressure difference across stations | Raw PR-AUC 0.4074908277100725; not selected; the original discussion notes a station-composition mismatch as a possible issue | variant_score_x2f.json |
| X1 scoring step | Average same-date station probabilities after neural prediction | W1 curve rises to PR-AUC 0.8302171573350975; this step does not retrain the network | variant_score_w3_x1.json |
| Recall-floor cutoff | Choose an alert cutoff that retains high event recall | 0.601 selected; TN 3386, FP 9, FN 4, TP 24; final original configuration | w1_recall_floor_report.json; THRESHOLD_CONFIG.md |

**X1 and X1f are different things.** X1 is a scoring step applied after a model produces probabilities. X1f is a separately trained model with extra pressure-change inputs. The names look similar, but they do not mean the same experiment. Likewise, “F1 model” means an alpha experiment, while “F1 score” means the precision/recall metric.

The original record reports W1 stopped at epoch 49, best epoch 37; W2 at epoch 35, best 23; W3 at epoch 19, best 7. These are the corrected September records. An earlier chat message incorrectly said W1 completed all 50; the original session later corrected it. No complete W2/W3 epoch curves were recovered as existing files.

### Full original comparison scorecards

“Cutoff” is chosen on TUNE for each row. A different cutoff can change the alert counts without changing PR-AUC. This table copies the original files, including unsuccessful alternatives.

| File / variant | Cutoff | TN | FP | FN | TP | Precision | Recall | F1 score | PR-AUC |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| [variant_score_f1.json](original_score_files/variant_score_f1.json) | 0.45 | 3362 | 33 | 4 | 24 | 0.42105263157894735 | 0.8571428571428571 | 0.5647058823529412 | 0.6417303783956378 |
| [variant_score_f1_x1.json](original_score_files/variant_score_f1_x1.json) | 0.48 | 3372 | 23 | 9 | 19 | 0.4523809523809524 | 0.6785714285714286 | 0.5428571428571429 | 0.6306273015378716 |
| [variant_score_f2.json](original_score_files/variant_score_f2.json) | 0.36 | 3376 | 19 | 8 | 20 | 0.5128205128205128 | 0.7142857142857143 | 0.5970149253731343 | 0.6796913426073594 |
| [variant_score_f2_x1.json](original_score_files/variant_score_f2_x1.json) | 0.43 | 3389 | 6 | 10 | 18 | 0.75 | 0.6428571428571429 | 0.6923076923076924 | 0.7295499756988006 |
| [variant_score_w10.json](original_score_files/variant_score_w10.json) | 0.56 | 3383 | 12 | 21 | 7 | 0.3684210526315789 | 0.25 | 0.2978723404255319 | 0.32418579787966995 |
| [variant_score_w10_x1.json](original_score_files/variant_score_w10_x1.json) | 0.58 | 3395 | 0 | 25 | 3 | 1.0 | 0.10714285714285714 | 0.19354838709677416 | 0.35647435946886047 |
| [variant_score_w3.json](original_score_files/variant_score_w3.json) | 0.64 | 3388 | 7 | 8 | 20 | 0.7407407407407407 | 0.7142857142857143 | 0.7272727272727273 | 0.7277791504254221 |
| [variant_score_w3_x1.json](original_score_files/variant_score_w3_x1.json) | 0.62 | 3388 | 7 | 8 | 20 | 0.7407407407407407 | 0.7142857142857143 | 0.7272727272727273 | 0.8302171573350975 |
| [variant_score_w6.json](original_score_files/variant_score_w6.json) | 0.58 | 3372 | 23 | 7 | 21 | 0.4772727272727273 | 0.75 | 0.5833333333333334 | 0.6402825755001175 |
| [variant_score_w6_x1.json](original_score_files/variant_score_w6_x1.json) | 0.61 | 3385 | 10 | 8 | 20 | 0.6666666666666666 | 0.7142857142857143 | 0.689655172413793 | 0.7168353098477321 |
| [variant_score_x1f.json](original_score_files/variant_score_x1f.json) | 0.62 | 3383 | 12 | 8 | 20 | 0.625 | 0.7142857142857143 | 0.6666666666666666 | 0.752289067711023 |
| [variant_score_x1f_x1.json](original_score_files/variant_score_x1f_x1.json) | 0.64 | 3387 | 8 | 9 | 19 | 0.7037037037037037 | 0.6785714285714286 | 0.6909090909090909 | 0.7976339658670485 |
| [variant_score_x2f.json](original_score_files/variant_score_x2f.json) | 0.66 | 3391 | 4 | 18 | 10 | 0.7142857142857143 | 0.35714285714285715 | 0.4761904761904762 | 0.4074908277100725 |
| [variant_score_x2f_x1.json](original_score_files/variant_score_x2f_x1.json) | 0.69 | 3393 | 2 | 24 | 4 | 0.6666666666666666 | 0.14285714285714285 | 0.23529411764705882 | 0.4734402971715002 |

These saved observations explain why W1+X1 was chosen in the original comparison. They do not, by themselves, prove that one intended code change caused the difference: different fresh trainings can also differ, and there was no fixed seed recorded for W1.

## Main record D. Exact original training, architecture, inputs, timing and score explanation

The next sections retain the original source-based explanation, including exact paths, training timestamps, settings, the first raw score, the final threshold rules and the original weather-score table.

## The exact training time I found

**W1 training launch was recorded on 15 September 2026 at 3:17:28.961 PM PHT. The model file was saved on 15 September 2026 at 4:16:46.778250800 PM PHT.** The first timestamp is the recorded launch command, not an instrumented timestamp of the first optimizer update. The second is the model filesystem timestamp captured in the original session.

The current model independently embeds `date_saved: 2026-09-15@16:16:46` in its Keras `metadata.json`. The original session’s file listing includes `+0800`, corroborating the local timezone. Its SHA-256 is `f2db5aa93226225405914094a0855ac725734a0e2c1a2331e3ba69a8fd9d14b0`, matching the W1 artifact documented at original selection. The launch-to-save interval was about 59 minutes.

**The original training-session file is:** [Original September training session (local source)](#source-register)

Go directly to line **26886** (launch), **26953** (completion and last epoch), and **26963** (exact saved-file timestamps). The session is JSONL: each physical line is a timestamped message or tool record. A small, relevant extract is provided in `ORIGINAL_W1_TIMELINE_EVIDENCE.json`, so you do not need to search the entire session.

## The original documentation to open first

| Original evidence | Exact existing local path |
|---|---|
| Original model-choice and threshold document | [THRESHOLD_CONFIG.md](#source-register) |
| Original trainer (verbatim local copy) | [_train_w3.py](#source-register) |
| Original X1 and recall-floor scorer (verbatim local copy) | [_w1_recall_floor.py](#source-register) |
| Original threshold sweep aggregate | [precision_floor_w3.json](#source-register) |
| Canonical physical/probability thresholds | [galecast_thresholds_w3.json](#source-register) |

The local copies listed above were checked byte-for-byte against `exp/precision-targeting`; all five match their git objects exactly. They were not reconstructed from later summaries. The original scripts are evidence to inspect; this scan did not execute them.

The original document `THRESHOLD_CONFIG.md` is the closest direct answer to “how did we arrive at the current model?” It identifies the trainer, explains the W1/W2/W3 naming, records the selected threshold, lists the tune/test results, documents the precision target shortfall, and states why the configuration was locked.

## Original chronology: built first, scored next, selected afterward

| Date and time, PHT | What the original evidence records | Source |
|---|---|---|
| 15 Sep 2026, 3:17:09.049 PM | W1/W2/W3 training scripts written | session line 26876 |
| 15 Sep 2026, 3:17:28.961 PM | W1 ×3 launch command | line 26886 |
| 15 Sep 2026, 3:17:48.119 PM | Progress output already shows Epoch 1/50 and training summary | line 26908 |
| 15 Sep 2026, 4:16:46.778250800 PM | W1 model saved, 571,546 bytes | captured file listing at line 26963; embedded model metadata agrees to the second |
| 15 Sep 2026, 4:17:12.039 PM | Completion confirmed; last epoch is 49/50 | line 26953 |
| 15 Sep 2026, 4:19:21.498287100 PM | First raw W1 score JSON saved | captured file listing at line 27038 |
| 17 Sep 2026, 4:22:27.604 PM | W1+X1 score output captured; PR-AUC 0.8302 | line 27816 |
| 17 Sep 2026, 4:42:05.669528600 PM | Recall-floor report saved | captured file listing at line 27984 |
| 17 Sep 2026, 5:49:35.214 PM | Original discussion corrects epoch count: 49, best epoch 37 | line 28224 |
| 17 Sep 2026, 11:17:13 +08:00 | W1+X1 configuration and provenance locked in commit f212f26 | original git commit; session line 28983 |

The current headline score therefore was not an automatically printed training accuracy at model-save time. The network was built on 15 September; its raw score was saved minutes later; X1 and the final recall-floor operating point were documented on 17 September. The model weights were reused for those scoring steps.

## What was trained

W1 is the **dual-stream ANN–LSTM–Attention model with 40,872 trainable parameters**. Its filename was `gale_cast_model_multioutput_w3.keras`; `_w3` means negative-class multiplier ×3. It is the model called **W1**, not the written-label W3. The current local filename is `gale_cast_model_multioutput.keras`.

| Component | Original construction |
|---|---|
| Normal input | 32 daily steps × 32 features |
| Normal branch | LSTM(64) → Dense(32, ReLU) |
| Anomaly input | 32 daily steps × 4 features |
| Anomaly branch | LSTM(32, return sequences) → exponential recency weights → learned attention over time → LSTM(32) → Dense(16, ReLU) |
| Shared layer | Concatenate the two branches, then Dropout 0.2 |
| Gale head | Dense(1, sigmoid): event probability |
| Weather head | Dense(6), custom output activations: wind speed, humidity, direction sine, direction cosine, rainfall transform, pressure |
| Optimizer | Adam |
| Losses | Focal loss gamma=2.0, alpha=0.75 for gale head; MSE with weight 0.3 for weather head |
| Training settings | Maximum 50 epochs; batch size 16 |
| Early stopping | Monitor `val_gale_prob_loss`; patience 12; restore best weights |
| Actual stopping | Epoch 49; best epoch 37, according to the original corrected record |
| Class-weight settings | Balanced weights; class 1 ×1.3, class 2 ×1.5, negative class ×3 |

Both the original training output and the saved model configuration support this architecture. The original trainer is `_train_w3.py`, not whichever training script happens to be open in the active branch now. The exact source blob is `d230a029c53eb7cc77b8bb10dbec0fbb1b3812e0`.

The original session first said “full 50 epochs” at line 26961, then explicitly corrected it at line 28224. The recorded last epoch is 49, so the corrected value is used here. The separate historical `dataset_audit.log` was not used as the W1 training log.

## Data and original tuning choices

Original primary-station training used dates before 2020-10-15, with Port Area and supplementary-station rows also included. The original run printed **78,955 combined rows** (9,567 real + 69,388 supplementary), **78,219 initial 32-day sequences**, and **1,133 initially gale-marked training chunks**. Those are separate stages of the pipeline, not interchangeable sample counts; subsequent weighting/augmentation code appears in the trainer.

Early stopping used the original TUNE year, 2020-10-15 through 2021-10-14. The original reported TEST slice begins 2021-10-15. Its three scored stations are NAIA, Sangley Point and Science Garden, with **3,423 scored windows and 28 positive labels**. The label is the project’s next-day wind/pressure threshold rule; the original document’s word “gale” refers to that study label.

The original W1 changes were recipe changes around this architecture: separate training/tuning dates, next-day labels, and the ×3 negative-class setting. The subsequent X1 step averaged same-date probabilities across the three stations. It did not add a neural layer or new trainable weights. The original threshold sweep then chose where on that probability curve to issue an alert.

## The first score immediately after training

The original `variant_score_w3.json` was written on **15 September at 4:19:21.498 PM PHT**, about two and a half minutes after the model save. This is the closest saved post-build score record. The scorer selected **0.64** by maximum F1 on TUNE (largest cutoff among ties).

| Original raw W1 result | Value |
|---|---:|
| TUNE threshold | 0.64 |
| TUNE TN / FP / FN / TP | 1071 / 2 / 2 / 17 |
| TUNE precision / recall / F1 | 0.8947368421052632 / 0.8947368421052632 / 0.8947368421052632 |
| TEST TN / FP / FN / TP | 3388 / 7 / 8 / 20 |
| TEST precision | 0.7407407407407407 |
| TEST recall | 0.7142857142857143 |
| TEST F1 | 0.7272727272727273 |
| TEST PR-AUC | 0.7277791504254221 |

This raw result is different from today’s familiar 72.73% precision / 85.71% recall headline because the headline uses X1 plus a different decision threshold. It is still the same W1 neural artifact.

## How the original selection reached W1+X1 at 0.601

The contemporaneous experiment compared negative-class multipliers **W1=×3**, **W2=×6**, and **W3=×10**, and then applied X1 to their probabilities. The original saved curves are:

| Original variant | Raw TEST PR-AUC | With X1 TEST PR-AUC |
|---|---:|---:|
| W1 / _w3 / ×3 | 0.7277791504254221 | 0.8302171573350975 |
| W2 / _w6 / ×6 | 0.6402825755001175 | 0.7168353098477321 |
| W3 / _w10 / ×10 | 0.32418579787966995 | 0.35647435946886047 |

The original session identifies W1+X1 as the strongest probability ranking in this comparison. It records that W2’s extra negative weighting reduced its score and that W3 reduced it further. Original F1/F2 and X1f/X2f experiments are also retained on the branch; they did not surpass W1+X1 in the saved September leaderboard. This states what the comparison observed, rather than proving which internal change caused it.

X1 increased W1’s saved TEST PR-AUC from **0.7277791504254221** to **0.8302171573350975**. The initial X1 maximum-F1 operating point had threshold 0.62 and still returned TP=20, FP=7. The recall-floor selection then moved the cutoff to **0.601**, catching 24 of the 28 positives while accepting 9 false positives.

The original documentation says three tuning-only rules converged on 0.601: R-FP12 (lowest cutoff satisfying a scaled false-alarm budget of 12), R-FP10 (budget 10), and R-REC85 (highest precision among thresholds meeting recall ≥0.85). The grid ran 0.001–0.999. TUNE at that cutoff was TN=1070, FP=3, FN=1, TP=18; precision 0.8571428571428571, recall 0.9473684210526315, F1 0.9. `w1_recall_floor_report.json` is the original saved proof of that convergence.

Changing the cutoff changed the confusion matrix, not PR-AUC: PR-AUC summarizes the ranked probabilities across cutoffs. The original record explicitly makes this distinction on 17 September.

## Original locked scorecard

| Metric | Original saved value |
|---|---:|
| Threshold | 0.601 |
| TN / FP / FN / TP | 3386 / 9 / 4 / 24 |
| Accuracy | 99.62% |
| Precision | 72.73% |
| Recall | 85.71% |
| F1 | 78.69% |
| PR-AUC | 0.8302 |

The counts explain the rounded metrics: accuracy = (3386+24)/3423, precision = 24/(24+9), recall = 24/(24+4), F1 = 2×24/(2×24+9+4). PR-AUC comes from the saved probability scores, not those four counts. The original write-up explicitly says precision was **2.27 percentage points below the 75% target**, rather than claiming that target was met.

### Weather scores stored with the original locked artifact

The branch’s `validation_cm3_w3.json` also stores the following regression block. These are the original recorded scorecard values; the training completion output itself does not print them as final physical-unit metrics. The separate wind-direction training script and custom output transformations should be consulted when attributing a row to an individual head or pipeline stage.

| Variable | MAE | RMSE | MASE | Saved unit label |
|---|---:|---:|---:|---|
| wind_speed | 0.5365 | 0.7723 | 0.6782 | m/s |
| humidity | 4.9453 | 6.417 | 0.6546 | % |
| wind_dir | 43.4016 | 62.9671 | 0.8497 | ° |
| rainfall | 0.9191 | 1.2747 | 0.9415 | mm |
| pressure | 1.2452 | 1.6919 | 0.5793 | hPa |

MAE is the mean absolute prediction error; RMSE is the square root of mean squared error. The table preserves the original MASE field without bringing in subsequent comparison work. The original classifier score provenance is pinned to the X1 scorer; the full regression post-processing derivation is not specified in `THRESHOLD_CONFIG.md`, so that document alone cannot establish that every weather row is a raw neural-head score. 

## Exact branch-only evidence references

Some original result files are preserved in local git history rather than as ordinary files in the active checkout. Read them with `git show exp/precision-targeting:<path>`, from the project folder, without switching branches.

- `exp/precision-targeting:THRESHOLD_CONFIG.md`
- `exp/precision-targeting:experiments/w1x1/_train_w3.py`
- `exp/precision-targeting:experiments/w1x1/_w1_recall_floor.py`
- `exp/precision-targeting:variant_score_w3.json`
- `exp/precision-targeting:variant_score_w3_x1.json`
- `exp/precision-targeting:w1_recall_floor_report.json`
- `exp/precision-targeting:precision_floor_w3.json`
- `exp/precision-targeting:precision_floor_w6.json`
- `exp/precision-targeting:precision_floor_w10.json`
- `exp/precision-targeting:validation_cm3_w3.json`
- `exp/precision-targeting:validation_cm3_interim_w3.json`
- `exp/precision-targeting:validation_cm3_v11.json`
- `exp/precision-targeting:validation_cm3_v12.json`
- `exp/precision-targeting:validation_cm3_v13.json`
- `exp/precision-targeting:validation_cm3_v14.json`
- `exp/precision-targeting:pre_registration_x_sweep.json`
- `exp/precision-targeting:x_sweep_recall_floor.json`
- `exp/precision-targeting:precision80_investigation.json`
- `exp/precision-targeting:galecast_thresholds_f1.json`
- `exp/precision-targeting:galecast_thresholds_f2.json`
- `exp/precision-targeting:galecast_thresholds_x1f.json`
- `exp/precision-targeting:galecast_thresholds_x2f.json`

## What the original files establish, and the remaining gap

The evidence establishes the recorded launch time, exact captured model-save time, saved artifact identity, architecture and settings, epoch-49 completion, first raw score, original W-variant comparison, X1 score gain, 0.601 threshold choice, and original configuration-lock date. This is a contemporaneous training-and-selection trail, not an explanation assembled from later comparison studies.

The standalone original `train_w3_run.log` scratch path was recorded in September but was not found as an existing file during this scan. Its completion output, epoch-count checks and model-file timestamps survive inside the original session JSONL. The session also preserves training-progress excerpts. An exact first-optimizer-update time and an independently complete 49-epoch history were not located as standalone files. No whole-network training seed was found. The noise generator’s separate seed 42 is documented above.

No existing file was changed, moved or deleted. No notebook, model, scoring script or database operation was executed. Only new report artifacts were written outside the project.

## Downloads

- [ORIGINAL_W1_SOURCE_PATHS.txt](downloads/SOURCE_REGISTER.txt) — Exact original-source paths and local git references
- [ORIGINAL_W1_TIMELINE_EVIDENCE.json](downloads/ORIGINAL_W1_TIMELINE_EVIDENCE.json) — Timestamped excerpts from the original September session
- [ORIGINAL_W1_SAVED_SCORES.json](downloads/ORIGINAL_W1_SAVED_SCORES.json) — Original scorecards and W-variant curve summaries
- [ORIGINAL_W1_SOURCE_IDENTITY.json](downloads/ORIGINAL_W1_SOURCE_IDENTITY.json) — Byte-identity checks for the original local source copies

## Main record E. What the current model reads, in basic English

W1 reads a 32-day history. The normal branch has 24 local weather/derived columns plus eight lagged direction columns from four stations. The anomaly branch focuses on four changing-weather signals. A “lag 1” means the previous day; “lag 2” means two days earlier. A rolling average or maximum summarizes recent days. Sine/cosine encode a repeating direction or season without a sharp break at its end.

| Input group | Actual original input names | Why this group is present |
|---|---|---|
| Main weather | wind_speed, rainfall, mean_sea_level_pressure, relative_humidity | Describe the recent weather state |
| Changes | wind_acceleration, pressure_tendency, pressure_drop, rainfall_change, humidity_change | Describe how weather is changing |
| Recent history | humidity_lag1, humidity_lag2, humidity_7day_avg, wind_speed_3day_avg, wind_speed_3day_max, wind_std_3, wind_speed_lag1, wind_speed_lag2, pressure_lag1 | Give the network short-term history and variability |
| Season and flags | month_sin, month_cos, heavy_rain_flag, low_pressure_flag, storm_signal, precip_anomaly | Describe the season and engineered event/weather signals |
| Other-station direction | SG, NA, SP, PA direction sine/cosine at lag 1: eight columns | Supply previous-day direction information across stations |
| Anomaly branch | pressure_tendency, precip_anomaly, pressure_drop, storm_signal | Give the second branch a smaller set of changing-weather signals |

The presence of an input does not prove how important it was. The original architecture learns its combinations during training. No reliable original per-feature importance ranking was located for this W1 artifact.

## Appendix A. All available notebook epoch tables

Each table below belongs to its saved notebook/cell, not automatically to W1. The full CSV keeps the other metric columns. When a file has more than one training segment, the cell and segment are kept separate. Identical values across notebook versions are labelled above; they are not counted as proof of fresh training.

### galecast_v1.0.ipynb

Source: [galecast_v1.0.ipynb](#source-register). 7 saved summary rows. Same extracted sequence first seen in galecast_v1.0.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.0544 | 0.0444 | — |
| cell 2 / 1 | 2 | 0.05 | 0.0381 | — |
| cell 2 / 1 | 3 | 0.0475 | 0.039 | — |
| cell 2 / 1 | 4 | 0.0454 | 0.0427 | — |
| cell 2 / 1 | 5 | 0.0441 | 0.0451 | — |
| cell 2 / 1 | 6 | 0.0413 | 0.0482 | — |
| cell 2 / 1 | 7 | 0.0396 | 0.0428 | — |

### galecast_v2.0.ipynb

Source: [galecast_v2.0.ipynb](#source-register). 10 saved summary rows. Same extracted sequence first seen in galecast_v2.0.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.0619 | 0.0538 | — |
| cell 2 / 1 | 2 | 0.0614 | 0.0541 | — |
| cell 2 / 1 | 3 | 0.0614 | 0.0542 | — |
| cell 2 / 1 | 4 | 0.0614 | 0.0549 | — |
| cell 2 / 1 | 5 | 0.0614 | 0.0535 | — |
| cell 2 / 1 | 6 | 0.0614 | 0.0536 | — |
| cell 2 / 1 | 7 | 0.0614 | 0.0536 | — |
| cell 2 / 1 | 8 | 0.0613 | 0.0538 | — |
| cell 2 / 1 | 9 | 0.0613 | 0.0539 | — |
| cell 2 / 1 | 10 | 0.0614 | 0.0536 | — |

### galecast_v2.5.ipynb

Source: [galecast_v2.5.ipynb](#source-register). 25 saved summary rows. Same extracted sequence first seen in galecast_v2.5.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.0204 | 0.0864 | — |
| cell 2 / 1 | 2 | 0.019 | 0.0818 | — |
| cell 2 / 1 | 3 | 0.0188 | 0.0877 | — |
| cell 2 / 1 | 4 | 0.0185 | 0.0826 | — |
| cell 2 / 1 | 5 | 0.0187 | 0.0854 | — |
| cell 2 / 1 | 6 | 0.012 | 0.0645 | — |
| cell 2 / 1 | 7 | 0.0053 | 0.0312 | — |
| cell 2 / 1 | 8 | 0.0042 | 0.0287 | — |
| cell 2 / 1 | 9 | 0.0036 | 0.0245 | — |
| cell 2 / 1 | 10 | 0.0031 | 0.0219 | — |
| cell 2 / 1 | 11 | 0.0025 | 0.0216 | — |
| cell 2 / 1 | 12 | 0.0021 | 0.0174 | — |
| cell 2 / 1 | 13 | 0.002 | 0.0147 | — |
| cell 2 / 1 | 14 | 0.0017 | 0.0196 | — |
| cell 2 / 1 | 15 | 0.0017 | 0.0133 | — |
| cell 2 / 1 | 16 | 0.0016 | 0.0166 | — |
| cell 2 / 1 | 17 | 0.0014 | 0.0135 | — |
| cell 2 / 1 | 18 | 0.0013 | 0.0177 | — |
| cell 2 / 1 | 19 | 0.0013 | 0.0131 | — |
| cell 2 / 1 | 20 | 0.0012 | 0.012 | — |
| cell 2 / 1 | 21 | 0.0011 | 0.0139 | — |
| cell 2 / 1 | 22 | 0.0011 | 0.0199 | — |
| cell 2 / 1 | 23 | 0.001 | 0.0223 | — |
| cell 2 / 1 | 24 | 0.00098144 | 0.0251 | — |
| cell 2 / 1 | 25 | 0.0009906 | 0.0173 | — |

### galecast_v2.6.ipynb

Source: [galecast_v2.6.ipynb](#source-register). 14 saved summary rows. Same extracted sequence first seen in galecast_v2.6.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 3 / 1 | 1 | 0.0236 | 0.0559 | — |
| cell 3 / 1 | 2 | 0.006 | 0.0357 | — |
| cell 3 / 1 | 3 | 0.0046 | 0.0295 | — |
| cell 3 / 1 | 4 | 0.004 | 0.0278 | — |
| cell 3 / 1 | 5 | 0.0036 | 0.0273 | — |
| cell 3 / 1 | 6 | 0.0029 | 0.0187 | — |
| cell 3 / 1 | 7 | 0.0024 | 0.0197 | — |
| cell 3 / 1 | 8 | 0.0021 | 0.023 | — |
| cell 3 / 1 | 9 | 0.0019 | 0.0132 | — |
| cell 3 / 1 | 10 | 0.0018 | 0.0146 | — |
| cell 3 / 1 | 11 | 0.0016 | 0.0166 | — |
| cell 3 / 1 | 12 | 0.0015 | 0.0235 | — |
| cell 3 / 1 | 13 | 0.0013 | 0.0177 | — |
| cell 3 / 1 | 14 | 0.0014 | 0.0245 | — |

### galecast_v2.7.ipynb

Source: [galecast_v2.7.ipynb](#source-register). 14 saved summary rows. Same extracted sequence first seen in galecast_v2.7.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 3 / 1 | 1 | 0.0205 | 0.085 | — |
| cell 3 / 1 | 2 | 0.0056 | 0.034 | — |
| cell 3 / 1 | 3 | 0.0043 | 0.0248 | — |
| cell 3 / 1 | 4 | 0.0036 | 0.0195 | — |
| cell 3 / 1 | 5 | 0.0029 | 0.0207 | — |
| cell 3 / 1 | 6 | 0.0024 | 0.022 | — |
| cell 3 / 1 | 7 | 0.0021 | 0.0201 | — |
| cell 3 / 1 | 8 | 0.0019 | 0.018 | — |
| cell 3 / 1 | 9 | 0.0018 | 0.0153 | — |
| cell 3 / 1 | 10 | 0.0016 | 0.0156 | — |
| cell 3 / 1 | 11 | 0.0016 | 0.0156 | — |
| cell 3 / 1 | 12 | 0.0014 | 0.0194 | — |
| cell 3 / 1 | 13 | 0.0013 | 0.0229 | — |
| cell 3 / 1 | 14 | 0.0013 | 0.0161 | — |

### galecast_v2.8.ipynb

Source: [galecast_v2.8.ipynb](#source-register). 14 saved summary rows. Same extracted sequence first seen in galecast_v2.7.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.0205 | 0.085 | — |
| cell 2 / 1 | 2 | 0.0056 | 0.034 | — |
| cell 2 / 1 | 3 | 0.0043 | 0.0248 | — |
| cell 2 / 1 | 4 | 0.0036 | 0.0195 | — |
| cell 2 / 1 | 5 | 0.0029 | 0.0207 | — |
| cell 2 / 1 | 6 | 0.0024 | 0.022 | — |
| cell 2 / 1 | 7 | 0.0021 | 0.0201 | — |
| cell 2 / 1 | 8 | 0.0019 | 0.018 | — |
| cell 2 / 1 | 9 | 0.0018 | 0.0153 | — |
| cell 2 / 1 | 10 | 0.0016 | 0.0156 | — |
| cell 2 / 1 | 11 | 0.0016 | 0.0156 | — |
| cell 2 / 1 | 12 | 0.0014 | 0.0194 | — |
| cell 2 / 1 | 13 | 0.0013 | 0.0229 | — |
| cell 2 / 1 | 14 | 0.0013 | 0.0161 | — |

### galecast_v2.9.ipynb

Source: [galecast_v2.9.ipynb](#source-register). 18 saved summary rows. Same extracted sequence first seen in galecast_v2.9.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.0577 | 0.0335 | — |
| cell 2 / 1 | 2 | 0.0249 | 0.0181 | — |
| cell 2 / 1 | 3 | 0.0167 | 0.0097 | — |
| cell 2 / 1 | 4 | 0.0143 | 0.0125 | — |
| cell 2 / 1 | 5 | 0.0129 | 0.0243 | — |
| cell 2 / 1 | 6 | 0.0125 | 0.0069 | — |
| cell 2 / 1 | 7 | 0.0119 | 0.0063 | — |
| cell 2 / 1 | 8 | 0.0115 | 0.0078 | — |
| cell 2 / 1 | 9 | 0.0113 | 0.0106 | — |
| cell 2 / 1 | 10 | 0.0107 | 0.0094 | — |
| cell 2 / 1 | 11 | 0.0106 | 0.0061 | — |
| cell 2 / 1 | 12 | 0.0102 | 0.0084 | — |
| cell 2 / 1 | 13 | 0.01 | 0.0048 | — |
| cell 2 / 1 | 14 | 0.0099 | 0.0054 | — |
| cell 2 / 1 | 15 | 0.0096 | 0.0054 | — |
| cell 2 / 1 | 16 | 0.0094 | 0.0074 | — |
| cell 2 / 1 | 17 | 0.0093 | 0.0068 | — |
| cell 2 / 1 | 18 | 0.0094 | 0.0056 | — |

### galecast_v2.10.ipynb

Source: [galecast_v2.10.ipynb](#source-register). 10 saved summary rows. Same extracted sequence first seen in galecast_v2.10.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.0661 | 0.0577 | — |
| cell 2 / 1 | 2 | 0.0643 | 0.0523 | — |
| cell 2 / 1 | 3 | 0.0641 | 0.0481 | — |
| cell 2 / 1 | 4 | 0.0641 | 0.0509 | — |
| cell 2 / 1 | 5 | 0.0641 | 0.0478 | — |
| cell 2 / 1 | 6 | 0.064 | 0.0527 | — |
| cell 2 / 1 | 7 | 0.064 | 0.0544 | — |
| cell 2 / 1 | 8 | 0.0639 | 0.0547 | — |
| cell 2 / 1 | 9 | 0.0639 | 0.0509 | — |
| cell 2 / 1 | 10 | 0.0639 | 0.0573 | — |

### galecast_v2.11.ipynb

Source: [galecast_v2.11.ipynb](#source-register). 40 saved summary rows. Same extracted sequence first seen in galecast_v2.11.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.0696 | 0.0631 | — |
| cell 2 / 1 | 2 | 0.0473 | 0.0302 | — |
| cell 2 / 1 | 3 | 0.0234 | 0.0173 | — |
| cell 2 / 1 | 4 | 0.0171 | 0.0123 | — |
| cell 2 / 1 | 5 | 0.0143 | 0.0071 | — |
| cell 2 / 1 | 6 | 0.0131 | 0.0075 | — |
| cell 2 / 1 | 7 | 0.0123 | 0.0086 | — |
| cell 2 / 1 | 8 | 0.012 | 0.0086 | — |
| cell 2 / 1 | 9 | 0.012 | 0.0065 | — |
| cell 2 / 1 | 10 | 0.0115 | 0.0066 | — |
| cell 2 / 1 | 11 | 0.0109 | 0.0061 | — |
| cell 2 / 1 | 12 | 0.0109 | 0.0068 | — |
| cell 2 / 1 | 13 | 0.0102 | 0.0076 | — |
| cell 2 / 1 | 14 | 0.01 | 0.006 | — |
| cell 2 / 1 | 15 | 0.0099 | 0.0063 | — |
| cell 2 / 1 | 16 | 0.0098 | 0.0046 | — |
| cell 2 / 1 | 17 | 0.0094 | 0.0046 | — |
| cell 2 / 1 | 18 | 0.0093 | 0.0047 | — |
| cell 2 / 1 | 19 | 0.0092 | 0.0046 | — |
| cell 2 / 1 | 20 | 0.009 | 0.0063 | — |
| cell 2 / 1 | 21 | 0.009 | 0.0048 | — |
| cell 2 / 1 | 22 | 0.0088 | 0.0046 | — |
| cell 2 / 1 | 23 | 0.0087 | 0.0062 | — |
| cell 2 / 1 | 24 | 0.0085 | 0.0045 | — |
| cell 2 / 1 | 25 | 0.0085 | 0.0046 | — |
| cell 2 / 1 | 26 | 0.0083 | 0.0049 | — |
| cell 2 / 1 | 27 | 0.0083 | 0.0056 | — |
| cell 2 / 1 | 28 | 0.0082 | 0.0046 | — |
| cell 2 / 1 | 29 | 0.008 | 0.0044 | — |
| cell 2 / 1 | 30 | 0.0079 | 0.0043 | — |
| cell 2 / 1 | 31 | 0.0081 | 0.0047 | — |
| cell 2 / 1 | 32 | 0.0079 | 0.0055 | — |
| cell 2 / 1 | 33 | 0.0078 | 0.007 | — |
| cell 2 / 1 | 34 | 0.0078 | 0.006 | — |
| cell 2 / 1 | 35 | 0.0076 | 0.0042 | — |
| cell 2 / 1 | 36 | 0.0076 | 0.0055 | — |
| cell 2 / 1 | 37 | 0.0074 | 0.0046 | — |
| cell 2 / 1 | 38 | 0.0073 | 0.0043 | — |
| cell 2 / 1 | 39 | 0.0076 | 0.0052 | — |
| cell 2 / 1 | 40 | 0.0073 | 0.0113 | — |

### galecast_v3.0.ipynb

Source: [galecast_v3.0.ipynb](#source-register). 34 saved summary rows. Same extracted sequence first seen in galecast_v3.0.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.0688 | 0.0415 | — |
| cell 2 / 1 | 2 | 0.0341 | 0.0217 | — |
| cell 2 / 1 | 3 | 0.0224 | 0.0221 | — |
| cell 2 / 1 | 4 | 0.016 | 0.0088 | — |
| cell 2 / 1 | 5 | 0.0141 | 0.0083 | — |
| cell 2 / 1 | 6 | 0.0132 | 0.0078 | — |
| cell 2 / 1 | 7 | 0.0121 | 0.0084 | — |
| cell 2 / 1 | 8 | 0.0113 | 0.0067 | — |
| cell 2 / 1 | 9 | 0.0109 | 0.0117 | — |
| cell 2 / 1 | 10 | 0.0108 | 0.0072 | — |
| cell 2 / 1 | 11 | 0.0103 | 0.0084 | — |
| cell 2 / 1 | 12 | 0.01 | 0.0086 | — |
| cell 2 / 1 | 13 | 0.0096 | 0.0054 | — |
| cell 2 / 1 | 14 | 0.0098 | 0.0071 | — |
| cell 2 / 1 | 15 | 0.0094 | 0.0102 | — |
| cell 2 / 1 | 16 | 0.0093 | 0.0056 | — |
| cell 2 / 1 | 17 | 0.009 | 0.0065 | — |
| cell 2 / 1 | 18 | 0.0088 | 0.0056 | — |
| cell 3 / 1 | 1 | 0.0886 | 0.0793 | 0.0616 |
| cell 3 / 1 | 2 | 0.0665 | 0.0508 | 0.0335 |
| cell 3 / 1 | 3 | 0.0425 | 0.0375 | 0.0203 |
| cell 3 / 1 | 4 | 0.0357 | 0.0268 | 0.0098 |
| cell 3 / 1 | 5 | 0.0321 | 0.032 | 0.0147 |
| cell 3 / 1 | 6 | 0.0303 | 0.0244 | 0.0075 |
| cell 3 / 1 | 7 | 0.0292 | 0.0246 | 0.0081 |
| cell 3 / 1 | 8 | 0.0286 | 0.0255 | 0.0093 |
| cell 3 / 1 | 9 | 0.0273 | 0.0254 | 0.0098 |
| cell 3 / 1 | 10 | 0.0263 | 0.0211 | 0.0062 |
| cell 3 / 1 | 11 | 0.026 | 0.02 | 0.005 |
| cell 3 / 1 | 12 | 0.0256 | 0.021 | 0.006 |
| cell 3 / 1 | 13 | 0.0252 | 0.0208 | 0.0059 |
| cell 3 / 1 | 14 | 0.0249 | 0.0271 | 0.0123 |
| cell 3 / 1 | 15 | 0.0246 | 0.021 | 0.0064 |
| cell 3 / 1 | 16 | 0.0244 | 0.0217 | 0.007 |

### galecast_v3.1.ipynb

Source: [galecast_v3.1.ipynb](#source-register). 34 saved summary rows. Same extracted sequence first seen in galecast_v3.0.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.0688 | 0.0415 | — |
| cell 2 / 1 | 2 | 0.0341 | 0.0217 | — |
| cell 2 / 1 | 3 | 0.0224 | 0.0221 | — |
| cell 2 / 1 | 4 | 0.016 | 0.0088 | — |
| cell 2 / 1 | 5 | 0.0141 | 0.0083 | — |
| cell 2 / 1 | 6 | 0.0132 | 0.0078 | — |
| cell 2 / 1 | 7 | 0.0121 | 0.0084 | — |
| cell 2 / 1 | 8 | 0.0113 | 0.0067 | — |
| cell 2 / 1 | 9 | 0.0109 | 0.0117 | — |
| cell 2 / 1 | 10 | 0.0108 | 0.0072 | — |
| cell 2 / 1 | 11 | 0.0103 | 0.0084 | — |
| cell 2 / 1 | 12 | 0.01 | 0.0086 | — |
| cell 2 / 1 | 13 | 0.0096 | 0.0054 | — |
| cell 2 / 1 | 14 | 0.0098 | 0.0071 | — |
| cell 2 / 1 | 15 | 0.0094 | 0.0102 | — |
| cell 2 / 1 | 16 | 0.0093 | 0.0056 | — |
| cell 2 / 1 | 17 | 0.009 | 0.0065 | — |
| cell 2 / 1 | 18 | 0.0088 | 0.0056 | — |
| cell 3 / 1 | 1 | 0.0886 | 0.0793 | 0.0616 |
| cell 3 / 1 | 2 | 0.0665 | 0.0508 | 0.0335 |
| cell 3 / 1 | 3 | 0.0425 | 0.0375 | 0.0203 |
| cell 3 / 1 | 4 | 0.0357 | 0.0268 | 0.0098 |
| cell 3 / 1 | 5 | 0.0321 | 0.032 | 0.0147 |
| cell 3 / 1 | 6 | 0.0303 | 0.0244 | 0.0075 |
| cell 3 / 1 | 7 | 0.0292 | 0.0246 | 0.0081 |
| cell 3 / 1 | 8 | 0.0286 | 0.0255 | 0.0093 |
| cell 3 / 1 | 9 | 0.0273 | 0.0254 | 0.0098 |
| cell 3 / 1 | 10 | 0.0263 | 0.0211 | 0.0062 |
| cell 3 / 1 | 11 | 0.026 | 0.02 | 0.005 |
| cell 3 / 1 | 12 | 0.0256 | 0.021 | 0.006 |
| cell 3 / 1 | 13 | 0.0252 | 0.0208 | 0.0059 |
| cell 3 / 1 | 14 | 0.0249 | 0.0271 | 0.0123 |
| cell 3 / 1 | 15 | 0.0246 | 0.021 | 0.0064 |
| cell 3 / 1 | 16 | 0.0244 | 0.0217 | 0.007 |

### galecast_v3.2.ipynb

Source: [galecast_v3.2.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v3.3.ipynb

Source: [galecast_v3.3.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v4.0.ipynb

Source: [galecast_v4.0.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v4.1.ipynb

Source: [galecast_v4.1.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v4.2.ipynb

Source: [galecast_v4.2.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v4.3.ipynb

Source: [galecast_v4.3.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v4.4.ipynb

Source: [galecast_v4.4.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v4.5.ipynb

Source: [galecast_v4.5.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v4.6.ipynb

Source: [galecast_v4.6.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v4.7.ipynb

Source: [galecast_v4.7.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v4.8.ipynb

Source: [galecast_v4.8.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.0-SUMMER.ipynb

Source: [galecast_v5.0-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.1-SUMMER.ipynb

Source: [galecast_v5.1-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.2-SUMMER.ipynb

Source: [galecast_v5.2-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.3-SUMMER.ipynb

Source: [galecast_v5.3-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.4-SUMMER.ipynb

Source: [galecast_v5.4-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.5-SUMMER.ipynb

Source: [galecast_v5.5-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.6-SUMMER.ipynb

Source: [galecast_v5.6-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.7-SUMMER.ipynb

Source: [galecast_v5.7-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.8-SUMMER.ipynb

Source: [galecast_v5.8-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.9-SUMMER.ipynb

Source: [galecast_v5.9-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.10-SUMMER.ipynb

Source: [galecast_v5.10-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v5.11-SUMMER.ipynb

Source: [galecast_v5.11-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v6.0-SUMMER.ipynb

Source: [galecast_v6.0-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

### galecast_v6.1-SUMMER.ipynb

Source: [galecast_v6.1-SUMMER.ipynb](#source-register). 24 saved summary rows. Same extracted sequence first seen in galecast_v3.2.ipynb.

| Cell / segment | Epoch | Training loss | Validation loss | Validation gale loss |
|---|---:|---:|---:|---:|
| cell 2 / 1 | 1 | 0.088 | 0.0675 | 0.0456 |
| cell 2 / 1 | 2 | 0.0462 | 0.0451 | 0.0239 |
| cell 2 / 1 | 3 | 0.0357 | 0.0328 | 0.0119 |
| cell 2 / 1 | 4 | 0.0325 | 0.0318 | 0.0108 |
| cell 2 / 1 | 5 | 0.0309 | 0.0299 | 0.0082 |
| cell 2 / 1 | 6 | 0.029 | 0.0326 | 0.0125 |
| cell 2 / 1 | 7 | 0.0274 | 0.0259 | 0.0069 |
| cell 2 / 1 | 8 | 0.0264 | 0.0251 | 0.0083 |
| cell 2 / 1 | 9 | 0.0257 | 0.0265 | 0.0084 |
| cell 2 / 1 | 10 | 0.0251 | 0.0259 | 0.0092 |
| cell 2 / 1 | 11 | 0.025 | 0.0235 | 0.0065 |
| cell 2 / 1 | 12 | 0.0246 | 0.0239 | 0.0075 |
| cell 2 / 1 | 13 | 0.024 | 0.025 | 0.0078 |
| cell 2 / 1 | 14 | 0.0238 | 0.022 | 0.0055 |
| cell 2 / 1 | 15 | 0.0236 | 0.0232 | 0.0066 |
| cell 2 / 1 | 16 | 0.0233 | 0.0224 | 0.0058 |
| cell 2 / 1 | 17 | 0.023 | 0.0368 | 0.0197 |
| cell 2 / 1 | 18 | 0.0228 | 0.0242 | 0.006 |
| cell 2 / 1 | 19 | 0.0226 | 0.0209 | 0.0051 |
| cell 2 / 1 | 20 | 0.0224 | 0.0223 | 0.0056 |
| cell 2 / 1 | 21 | 0.0222 | 0.0222 | 0.006 |
| cell 2 / 1 | 22 | 0.022 | 0.0227 | 0.0057 |
| cell 2 / 1 | 23 | 0.0216 | 0.0277 | 0.0104 |
| cell 2 / 1 | 24 | 0.0218 | 0.0217 | 0.0059 |

## Appendix B. File index and what is still missing

The source index contains the exact local paths for notebooks, original scripts, original session records and model/score artifacts, plus git references for original files that exist only on another branch. Branch-only originals are read with `git show exp/precision-targeting:<path>`, without changing the checkout. The downloadable aggregate score copies include a manifest identifying the exact source and SHA-256.

The standalone original W1 training log was recorded in the September session but is no longer present at the recorded scratch path. Its surviving excerpts are preserved here. A complete score for every one of W1’s 49 epochs, a fixed whole-network W1 seed, a verified run date for every early notebook, and a fresh post-edit training output for every notebook version were not found. These gaps remain clearly marked.

Nothing in the project was trained, rescored, edited, moved or deleted. The updated report and companion files are in the separate report folder. The previous report version is kept as `ORIGINAL_W1_TRAINING_REPORT_v1.*`.

### Companion files

- [COMPLETE_ORIGINAL_FILE_INDEX.csv](downloads/SOURCE_REGISTER.csv) — All located original-development paths and duplicate locations, with file roles
- [COMPLETE_ORIGINAL_FILE_INDEX.txt](downloads/SOURCE_REGISTER.txt) — Same source index in plain text
- [EPOCH_RECORDS.csv](downloads/EPOCH_RECORDS.csv) — All 865 recovered metric-summary rows, with source and epoch labels; repeated rows retained
- [EPOCH_RECORDS.json](downloads/EPOCH_RECORDS.json) — Machine-readable metric records; unknown epoch/model stays unknown
- [TRAINING_VERSION_CHANGES.json](downloads/TRAINING_VERSION_CHANGES.json) — All 36 notebooks: observed settings, changes, hashes and repeated-output identity
- [ORIGINAL_W1_TIMELINE_EVIDENCE.json](downloads/ORIGINAL_W1_TIMELINE_EVIDENCE.json) — Original W1 timestamp proof
- [ORIGINAL_W1_SOURCE_IDENTITY.json](downloads/ORIGINAL_W1_SOURCE_IDENTITY.json) — Original trainer/scorer/document byte checks
- [ORIGINAL_SCORE_EXPORT_MANIFEST.json](downloads/ORIGINAL_SCORE_EXPORT_MANIFEST.json) — Exact git sources and hashes for all 23 original aggregate score/threshold exports
- [ORIGINAL_W1_TRAINING_REPORT.md](downloads/REPORT.md) — The complete report as editable plain text

## Appendix C. Source links for the follow-up findings

Original September session: [Original September training session (local source)](#source-register). Each line number above is the physical JSONL line in that file. The additional findings JSON supplies timestamps and a short explanation for each cited record.

Original W1 training code: [_train_w3.py](#source-register). Seed 42 for input-noise generation is on line 843 of that exact copy.

Original selection document: [THRESHOLD_CONFIG.md](#source-register). Original score and threshold code: [_w1_recall_floor.py](#source-register).

## Appendix D. What this file does not claim

- It does not claim a whole-network W1 seed was recovered.
- It does not claim that repeated notebook output proves each edited notebook was retrained.
- It does not invent numeric losses for the missing W1 epochs.
- It does not claim that the chosen layer sizes were proven optimal.
- It does not claim that every setting had a separate controlled ablation.
- It does not claim the recorded selection-period score is a new independent-test result.
- It does not claim that the located history proves there were no additional trials.

