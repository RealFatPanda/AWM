# Learning to Evade: Adaptive Attacks on Audio Watermarking

This paper has been accepted by Interspeech 2026 (long paper track). <br>

Our demo website [[demo]](https://adaptiveaudiowmattack.github.io/)

# How to Use
## Dependencies
```
conda create -n AWM python=3.9.21
conda activate AWM
pip install -r requirements.txt
pip install librosa==0.9.1
```

## Install ViSQOL
Please visit this website https://github.com/google/visqol

# Defender -- Outlier Detection
For watermarked audio
```
python outlier_detection/audioseal_p_value_detection.py
python outlier_detection/timbre_p_value_detection.py
```
For clean audio
```
python outlier_detection/audioseal_p_value_detection_clean.py
python outlier_detection/timbre_p_value_detection_clean.py
```

# Attacker
We put some audio files to the folder "attack_audioseal" and "attack_timbre", please change the audio directory in the function of "decode_audio_files_perturb_whitebox" before you run the python files.
## AWM
For example, for the watermark replacement, before running the command for the watermark replacement, change dataset in line 308 and 316.
```
python white-box/watermark_replacement.py --model audioseal --whitebox_folder attack_audioseal_replacement
python white-box/watermark_replacement.py --model timbre --whitebox_folder attack_timbre_replacement
```
Watermark Creation
```
python white-box/watermark_creation.py --model audioseal --whitebox_folder attack_audioseal_creation
python white-box/watermark_creation.py --model timbre --whitebox_folder attack_timbre_creation
```
Watermark Removal
```
python white-box/watermark_remove.py --model audioseal --whitebox_folder attack_audioseal_removal
python white-box/watermark_remove.py --model timbre --whitebox_folder attack_timbre_removal
```
## AWM (+opt)
For example, for the watermark replacement, change dataset to the benign watermarked data in line 220 and line 236, and the generated AWM adversarial data in line 225 and line 238.
```
python white-box/optimization_watermark_replacement.py --model audioseal --whitebox_folder attack_audioseal_replacement_optimization --dataset librispeech
python white-box/optimization_watermark_replacement.py --model timbre --whitebox_folder attack_timbre_replacement_optimization --dataset librispeech
```
Watermark Creation
```
python white-box/optimization_watermark_creation.py --model audioseal --whitebox_folder attack_audioseal_creation_optimization --dataset librispeech
python white-box/optimization_watermark_creation.py --model timbre --whitebox_folder attack_timbre_creation_optimization --dataset librispeech
```
Watermark Removal
```
python white-box/optimization_watermark_remove.py --model audioseal --whitebox_folder attack_audioseal_removal_optimization --dataset librispeech
python white-box/optimization_watermark_remove.py --model timbre --whitebox_folder attack_timbre_removal_optimization --dataset librispeech
```
# Acknowledgements
This implementation uses parts of the code from the following Github repos: [[AudioMarkBench]](https://github.com/moyangkuo/AudioMarkBench)
