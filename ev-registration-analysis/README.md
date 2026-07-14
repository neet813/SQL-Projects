# EV Registration Data Analysis

**Data source:** [Electric Vehicle Population Data — Washington State Dept. of Licensing, via data.gov](https://catalog.data.gov/dataset/electric-vehicle-population-data)

Analysis of 287,764 Battery Electric and Plug-in Hybrid vehicle registrations from the Washington State Department of Licensing.

## The Problem
The dataset looked ready to analyze on the surface, but running any calculation on it without first checking the data would risk producing a confident, wrong answer.

## Why I Approached It This Way

Before drawing any conclusion from a new dataset, I check whether it can actually be trusted — the same habit I use in my day-to-day retail data work, where an unverified number can mislead a client just as easily as it can mislead anyone here.

## How

**1. Investigated the "Electric Range" field.**
Found that 186,814 of 287,764 rows (65%) showed a value of `0` — not because those vehicles genuinely had zero range, but because the range had never been measured for them. Left unchecked, this would have silently dragged down any average calculation.

**2. Checked the rest of the dataset's structural integrity** before trusting it further — duplicate identifiers, brand-name consistency, and implausible model years. All came back clean.

**3. Rebuilt the average-range calculation** to exclude the placeholder zeros.
→ Corrected real-world average: **107.8 miles** (vs. a misleadingly low number if the placeholders had been included).

**4. Ranked vehicle makes by volume and true average range.**
→ Tesla led on both volume (118,575 vehicles, ~41% of the dataset) and range (241.6 miles average).

**5. Noticed an anomaly and chased it.**
Rivian returned no average at all — not zero, a true blank. Investigating further confirmed every single Rivian entry in this dataset had unmeasured range data — a real, reportable gap that a surface-level analysis would have missed entirely.

## Impact

The corrected analysis avoided a materially wrong conclusion — a naive average would have understated real-world EV range purely from unflagged placeholder data. The Rivian finding reflects a broader habit: verifying *why* a result looks unusual rather than accepting a blank or unexpected number at face value.
