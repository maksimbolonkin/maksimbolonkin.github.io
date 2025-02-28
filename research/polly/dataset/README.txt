Political Lying from Videos (POLLY) Dataset

1. Dataset is fully described in the file dataset.csv. This file contains the following columns:
subject_name: name of the politician
video_url: URL of the original video
clip_start: time stamp of the start of the relevant clip
clip_end: time stamps of the end of the relevant clip
label: True or False
verification_url: URL of the fact-checking source for deceptive messages
country: country of origin of the corresponding subject
language: original language of the recording

2. Video directory contains video clips from the dataset. Video file names are encoded as follows: [subject_name]_[label].mp4 (cf. dataset.csv). For example Aleksander_Vucic_F.mp4 is a clip for Aleksander Vucic with deceptive speech in it.

3. Audio directory contains audio files extracted from video clips.

4. Transcripts directory contains the following subdirectories:
 automated_translation: contains text files with transcripts where non-English texts are translated automatically
 mturk_translation: contains a subset of transcripts where non-English texts were translated by Amazon Mechanical Turk workers (NOTE: this directory does not contain files for transcripts that were originally in English)

5. Articles directory contains subdirectories one for each of the subjects (politicians) with text files containing articles referring to the subject (cf. the text of the paper for more explanations).

Copyright Notice
This dataset is distributed as is for research purpose only.