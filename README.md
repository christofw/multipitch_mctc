# Repository multipitch_mctc

This is a pytorch code repository accompanying the following paper:  

> Christof Weiß and Geoffroy Peeters  
> _Learning Multi-Pitch Estimation From Weakly Aligned Score-Audio Pairs Using a Multi-Label CTC Loss_  
> Proceedings of the IEEE Workshop on Applications of Signal Processing to Audio and Acoustics (WASPAA), 2021  

This repository only contains exemplary code and pre-trained models for most of the paper's experiments as well as some individual examples. All datasets used in the paper are publicly available (at least partially), e.g. our main datasets:
* [Schubert Winterreise Dataset (SWD)](https://zenodo.org/record/5139893#.YWRcktpBxaQ)
* [MusicNet](https://homes.cs.washington.edu/~thickstn/musicnet.html)
* [MAESTRO v3.0.0](https://magenta.tensorflow.org/datasets/maestro)
For details and references, please see the paper.

## Feature extraction and prediction (Jupyter notebooks)

In this top folder, two Jupyter notebooks (_01_precompute_features_ and _02_predict_with_pretrained_model_) demonstrate how to preprocess audio files for running our models and how to load a pretrained model for predicting pitches.

## Experiments from the paper (.py scripts)

In the _experiments_ folder, all experimental scripts as well as the log files (subfolder _logs_) and the filewise results (subfolder _results_filewise_) can be found. The folder _models_pretrained_ contain pre-trained models for the main experiments. The subfolder _predictions_ contains exemplary model predictions for two of the experiments. Plese note that re-training requires a GPU and that any script must be started from the repository top folder path in order to get the relative paths working correctly.

The experiment files' names relate to the paper's results in the following way:

### Experiment 1 (Table 2) - Loss and Model variants
exp112aS_traintest_schubert_aligned_pitch_nooverlap_segmmodel.pt (Strongly-aligned training (BCE loss))
* exp118b_traintest_schubert_sctcthreecomp_pitch.pt (Separable CTC (SCTC) loss)
* exp118d_traintest_schubert_mctcnethreecomp_pitch.pt (Non-Epsilon MCTC (MCTC:NE) loss)
* exp118e_traintest_schubert_mctcwe_pitch.pt (MCTC with epsilon (MCTC:WE) loss)

### Experiment 2 (Section 3.2) - Train/test on common datasets
* exp121a_traintest_musicnet_mctcwe_pitch_basiccnn.pt (Train/test MusicNet with strongly-aligned training)
* exp121cS_traintest_musicnet_aligned_pitch_basiccnn_segmmodel.pt (Train/test MusicNet with MCTC loss)
* exp122a_traintest_maestro_mctcwe_pitch_basiccnn.pt (Train/test MAESTRO with strongly-aligned training)
* exp122cS_traintest_maestro_aligned_pitch_basiccnn_segmmodel.pt (Train/test MAESTRO with MCTC loss)

### Experiment 3 (Figure 2) - Cross-dataset experiment
* exp123a_trainmaestromunet_testmix_mctcwe_pitch_basiccnn.pt (Train MusicNet & MAESTRO, test others, MCTC)
* exp123cS_trainmaestromunet_testmix_aligned_pitch_basiccnn_segmmodel.pt (Train MusicNet & MAESTRO, test others, aligned)
* exp124a_trainmix_testmusicnet_mctcwe_pitch_basiccnn.pt  (Test MusicNet, train others, MCTC)
* exp124cS_trainmix_testmusicnet_aligned_pitch_basiccnn_segmmodel.pt (Test MusicNet, train others aligned)
* exp125a_trainmix_testmaestro_mctcwe_pitch_basiccnn.pt (Test MAESTRO, train others MCTC)
* exp125cS_trainmix_testmaestro_aligned_pitch_basiccnn_segmmodel.pt (Test MAESTRO, train others aligned)
