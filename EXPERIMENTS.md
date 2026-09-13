RSNA Knee high-score baseline

Source baseline: mattiaangeli/bend-the-knee-to-the-dinosaurs
Publicly documented progression: 0.937 -> 0.940 -> 0.941.

Experiment knobs to isolate in future runs:
- DINOv3 blend weight
- RadImageNet E13/E10 blend weights
- CoAtNet arm weights and reverse-view arm
- per-target outer routing, especially meniscus/OA labels

Current controlled experiment:
- E10 twin-head branch promoted to the primary transformer artifact.
- The V48 pass-2/calibrated reference artifact is retained as `submission_reference_calibrated.csv` for rollback and comparison.
- Raptor/CoAtNet routing remains unchanged from the 0.940 incumbent.

Promotion gate:
- The remote kernel must complete successfully.
- Primary `submission.csv` must pass the 3-study × 13-column schema, UID-order, finite-value, and `[0, 1]` checks.
- Only a completed public Kaggle score can promote or reject the variant.

Latest controlled candidate:
- Public kernel: `nishantkharga/rsna-knee-full-4-arm-ensemble-v55`, version `1`
- Hypothesis: a materially different full four-arm ensemble can improve the 0.940 incumbent by adding the complete DINOv2 + A5 DINOv3 + RadImageNet V18 + dual CoAtNet path.
- Output SHA-256: `d8d5d97ac70509d77644e534de8f374355ee65389c46dd662c5f5938b943895a`
- Local audit: passed exact sample schema and UID order, 3 rows × 13 columns, unique UIDs, finite values in `[0, 1]`, and no fallback studies.
- Distinctness: 11 of 36 prediction cells differ from the E10 output; Tonylica's 41-member notebook was byte-identical to E10 and the lateral-meniscus fork was byte-identical to probe22, so neither was resubmitted.
- Submission: Kaggle `56206291`, submitted September 13, 2026; status `PENDING`; four submissions remain.
- Decision: `WATCH` until Kaggle returns a public score. Do not promote over the 0.940 incumbent while scoring is pending.

Coherence mark:
- Ensemble matches prior winner: false
- Latest candidate has fresh output identity: true
- Live promotion allowed: false
- Reason: public score and replay evidence are not yet available.
