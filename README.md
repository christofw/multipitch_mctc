# multipitch_mctc

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

## Experiments from the paper (Python scripts)

In the _experiments_ folder, all experimental scripts as well as the log files (subfolder _logs_) and the filewise results (subfolder _results_filewise_) can be found. The folder _models_pretrained_ contains pre-trained models for the main experiments. The subfolder _predictions_ contains exemplary model predictions for two of the experiments. Plese note that re-training requires a GPU as well as the pre-processed training data (see the notebook _01_precompute_features_ for an example). Any script must be started from the repository top folder path in order to get the relative paths working correctly.

The experiment files' names relate to the paper's results in the following way:

### Experiment 1 (Table 2) - Loss and Model variants
* _exp112aS_traintest_schubert_aligned_pitch_nooverlap_segmmodel.pt__ (Strongly-aligned training (BCE loss))
* _exp118b_traintest_schubert_sctcthreecomp_pitch.pt_ (Separable CTC (SCTC) loss)
* _exp118d_traintest_schubert_mctcnethreecomp_pitch.pt_ (Non-Epsilon MCTC (MCTC:NE) loss)
* _exp118e_traintest_schubert_mctcwe_pitch.pt_ (MCTC with epsilon (MCTC:WE) loss)

### Experiment 2 (Section 3.2) - Train/test on common datasets
* _exp121a_traintest_musicnet_mctcwe_pitch_basiccnn.pt_ (Train/test MusicNet with strongly-aligned training)
* _exp121cS_traintest_musicnet_aligned_pitch_basiccnn_segmmodel.pt_ (Train/test MusicNet with MCTC loss)
* _exp122a_traintest_maestro_mctcwe_pitch_basiccnn.pt_ (Train/test MAESTRO with strongly-aligned training)
* _exp122cS_traintest_maestro_aligned_pitch_basiccnn_segmmodel.pt_ (Train/test MAESTRO with MCTC loss)

### Experiment 3 (Figure 2) - Cross-dataset experiment
* _exp123a_trainmaestromunet_testmix_mctcwe_pitch_basiccnn.pt_ (Train MusicNet & MAESTRO, test others, MCTC)
* _exp123cS_trainmaestromunet_testmix_aligned_pitch_basiccnn_segmmodel.pt_ (Train MusicNet & MAESTRO, test others, aligned)
* _exp124a_trainmix_testmusicnet_mctcwe_pitch_basiccnn.pt_ (Test MusicNet, train others, MCTC)
* _exp124cS_trainmix_testmusicnet_aligned_pitch_basiccnn_segmmodel.pt_ (Test MusicNet, train others aligned)
* _exp125a_trainmix_testmaestro_mctcwe_pitch_basiccnn.pt_ (Test MAESTRO, train others MCTC)
* _exp125cS_trainmix_testmaestro_aligned_pitch_basiccnn_segmmodel.pt_ (Test MAESTRO, train others aligned)

Run scripts using e.g. the following commands:  
__conda activate multipitch_mctc__  
__export CUDA_VISIBLE_DEVICES=1__  
__python experiments/exp112aS_traintest_schubert_aligned_pitch_nooverlap_segmmodel.pt__  
