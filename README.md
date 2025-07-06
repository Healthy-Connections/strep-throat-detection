# Strep-Throat

Public Github repository for the strep throat detection paper.

This repository contains Python notebooks as well as models for training classification models and throat annotation generation.


## Data

Original Strep Throat dataset from Yoo et al. can be found [here](https://data.mendeley.com/datasets/8ynyhnj2kz/2).

Dataset splits and data augmentation is generated inside `STREPCLASSIFICATION.ipynb notebook`. 

Expert labelled medical sign annotations of validation and test images can be found within `data/Throat_Sign_Labels`.

Synthetic generation of annotations for train set of throat images can be generated using GPT-4o-mini using script at bottom of `Fine_tune_BLIP2.ipynb`.


## Usage

`STREPCLASSIFICATION.ipynb`
- Original experiments on strep throat dataset 
- Dataset splitting
- Data augmentation
- Cycle-GAN augmentation
- Grad-CAM visualisations
- Basic Model experiments


`Strep_Benchmark.ipynb`
- Scripts for performing benchmarking of strep throat classification task using various architectures
- Uses WandB for tracking experiments


`Fine_tune_BLIP2.ipynb`
- Experiments for using BLIP2 vision adapter with Meta OPT 2.7 billion parameter LLM
- Based off original methodology from [Younes Belkada](https://github.com/huggingface/notebooks/blob/main/peft/Fine_tune_BLIP2_on_an_image_captioning_dataset_PEFT.ipynb)
- Can be loaded on colab T4 GPU
- Uses LoRA to reduce trainable parameters for faster tuning
- Fine-tuned strep-throat model available on huggingface can be loaded in for use without training
- Scripts for using GPT-4o-mini for synthetic data generation for training BLIP2 model


`xai_validation`
- Scripts for evaluating performance of BLIP2 and GPT generated annotations
- Compares with expert labels stored in `data/Throat_Sign_Labels`
