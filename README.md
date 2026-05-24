# Dylan Carlson Swing Follow-Through Analysis

This project analyzes Dylan Carlson’s 2023 MLB swing follow-throughs using manually labeled video data joined to Baseball Savant/Statcast pitch-level data.

The main question: when Carlson finishes with one hand instead of two, is that just a result of pitch context, or is it associated with weaker contact quality even after accounting for Statcast variables?

## Project Summary

I manually labeled 482 Carlson swings from the 2023 season as one-hand, two-hand, check swing, bunt, or unusable. I then joined those labels to Statcast data using MLB `playId`s and analyzed whether follow-through type was related to contact quality, batting side, pitch location, count, and other pitch-context variables.

The analysis found that one-hand follow-throughs were associated with lower exit velocity and lower hard-hit probability, especially from the left side. After controlling for Statcast context with nested regression models, follow-through type still added explanatory value for contact-quality outcomes.

This should be interpreted as an association, not a causal claim. The project is a single-player case study, and follow-through type may reflect swing adjustment, pitch difficulty, timing, or other factors not fully captured in the data.

## What I Built

- Manually labeled swing follow-throughs from video
- Joined video-derived labels to Baseball Savant/Statcast pitch-level data
- Engineered variables for batting side, pitch context, contact quality, and swing outcomes
- Compared one-hand and two-hand follow-throughs using descriptive statistics and visualizations
- Ran nested regression models to test whether follow-through added information after Statcast context
- Explored an image-based machine learning pipeline for automating follow-through labels from swing frames

## Key Methods

- Data cleaning and feature engineering in R
- Manual video labeling
- Statcast pitch-level analysis
- Nested linear and logistic regression models
- Robustness checks by batting side and pitch context
- Exploratory computer vision workflow using Python, `yt-dlp`, `ffmpeg`, and PyTorch/ResNet18

## Main Takeaways

- Carlson’s follow-through type differed sharply by batting side.
- One-hand follow-throughs were linked to weaker contact-quality metrics in the 2023 sample.
- The left-handed sample provided the cleaner comparison because both follow-through types occurred frequently.
- Follow-through type still added explanatory value after controlling for Statcast pitch and count context.
- The computer vision work showed that automating labels is possible as a pipeline, but would need more data and a better temporal model before being reliable.


## Limitations

This is a single-player, single-season case study. The follow-through labels were manually created and are not official Statcast measurements. The results should be read as evidence of association, not proof that one follow-through mechanically causes better or worse contact.

## Tools Used

R, tidyverse, ggplot2, Baseball Savant/Statcast data, Python, MLB Stats API, `yt-dlp`, `ffmpeg`, PyTorch, ResNet18
