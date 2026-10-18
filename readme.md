# High Innovation! Fault Diagnosis Network Based on Time-Series-Time-Frequency Patch Interaction and Wavelet Convolution

Preface
Traditional fault diagnosis often follows two main paths: one approach directly processes raw vibration signals, relying on one-dimensional convolution, recurrent neural networks, or Transformer to learn the impact waveforms and time-dependent; the other approach first visualizes a one-dimensional signal image, then uses a two-dimensional vision network to extract texture, structure, and global patterns. Both approaches have their advantages but suffer from insufficient information utilization when used individually. To address this, we propose a multimodal fault diagnosis model for general-purpose fault diagnosis tasks: Patch-based Temporal–Field Wavelet Transformer Network (PatchTF-WTNet) for Periodic-Time-Frequency Image Cross-Modal Fusion Fault Diagnosis.
The PatchTF-WTNet is built around the "dual-modality collaborative diagnosis" framework. The model retains the original vibration signal as the first modality, using the Patch Transformer to model local impact segments and long-range dependencies across segments; at the same time, it utilizes a Markov transition field to map the same one-dimensional signal segment into a two-dimensional state transition image as the second modality, enhancing the visual branch's ability to perceive multiscale transfer textures and large-scale structures through Haar wavelet convolution. Subsequently, rather than simply concatenating the two branches, they achieve explicit information exchange through bidirectional cross-Patch attention, and use a gate mechanism to adaptively adjust the contribution of both modalities for each sample, ultimately completing fault category discrimination.
(Also provides multiple choice of time-frequency images)
Dataset: Dongxi University bearing dataset, CWRU West Reserve University bearing dataset
Environmental framework: Python 3.11, PyTorch 2.1 and above versions are all compatible
Accuracy: Test set 99%
Usage object: Paper requirements, graduation design requirements
● Code Guarantee: The code comments are detailed and ready to run.
1. Model Process Overview
1.1 Overall Model Process
- PatchTF-WTNe
The core idea of PatchTF-WTNe is: A multimodal intelligent classification network for bearing and rotating machinery fault diagnosis. The model uses raw one-dimensional vibration signals and Markov transition fields (MTF) two-dimensional state transition images as two complementary modalities: the sequential branch captures local impact patterns and cross-segment long-range dependencies through overlapping Patch Transformer; the image branch models MTF images with multiscale, multi-band visualization through Haar wavelet convolution networks. On this basis, PatchTF-WTNet designs a bidirectional cross-Patch attention mechanism that enables the original signal to actively query related MTF state transition textures in the local impact segments, while enabling the image modality to reference real waveform dynamics in reverse; subsequently, it adjusts the contribution of both modalities according to the current sample through feature-level gating mechanisms. The model constructs a complete diagnostic link from three levels: "Multimodal Complementary Representation—Patch Level Deep Interaction—Dynamic Modality Fusion," providing an expandable multimodal modeling framework for complex working conditions, noisy environments, and cross-domain fault diagnosis.
1.2 Model Innovation Points
Innovation Point One: Dual-modality complementary modeling of raw waveforms and MTF state transition images
Traditional fault diagnosis often learns features from a single data representation: directly inputting raw signals may focus on local waveforms, while only inputting two-dimensional images may weaken the details of the original impact. PatchTF-WTNet represents the same vibration signal as two modalities with different physical meanings.
Problem/Mechanism/Benefit logic:
Problem: Single-modal representation suffers from information bias, making it difficult to simultaneously utilize the raw waveform and global state transition structure;
Mechanism: Constructing the original signal with MTF images into a homogeneous heterogeneous dual-modal input;
Benefits: Retaining both local transient shocks and global state transition patterns, enhancing the completeness of fault characteristics and model robustness.
Innovation Point Two: Time-series patch transformer for local shock semantics - Fault vibration signals do not have equal diagnostic value at all sampling points, local shocks and their neighborhoods usually contain more stable fault modes. The model does not directly treat single points as tokens, but constructs overlapping patches, so one patch can establish connections with distant patches, allowing the model to learn both local shock segments and cross-period recurring patterns simultaneously.
Innovation Point Three: Haar wavelet convolution enhanced multi-scale visual coding in MTF - Fault patterns in MTF images are not only local textures but also may manifest as state transition structures across large areas. Regular small convolution kernels require stacking deeper networks to expand the receptive field, while simply increasing the kernel size significantly increases the parameter count. CatchTF-WTNet introduces multi-level Haar wavelet decomposition in the visual branch, breaking down features into low-frequency contours and three-directional high-frequency details. Through multiple decomposition levels, deep subbands correspond to larger effective regions of the original image. In simple terms, the k*k convolution kernel in the Lth level wavelet domain corresponds to an expanded sense range of the original image with increasing scale. Problem-mechanism-benefit logic:
Problem: MTF fault textures have both local and global coexistence, and multi-scale state transition structures;
Mechanism: By using Haar WT, different frequency/directional textures are decomposed, and in the multi-level wavelet domain, small kernel convolution achieves a larger effective sense range;
Benefit: While controlling the parameter scale, it enhances the joint perception of global contours, block transition structures, and high-frequency texture details in MTF.
3. Innovation Point Four: Bidirectional Cross-Patch Attention for Deep Modal Interaction
The PatchTF-WTNet implements bidirectional cross-modal attention at the token level. This allows the original signal patch to actively search for the MTF transfer texture regions most relevant to its fault mode, while the MTF image patch can also reversely reference the real impact dynamics in the original signal. Using bidirectional \"Cross-Attention\" at the \"token\" level for mutual query and mutual enhancement, it has been upgraded from "parallel use of two modalities" to "two modalities collaboratively interpreting the same fault," thereby enhancing the utilization rate of complementary information across modalities.
2 Data Preprocessing for Southeast University Dataset
2.1 Import Data
The Southeast University gearbox dataset includes two subdatasets: bearings and gears, both collected from a transmission system dynamics simulator. The gear fault dataset consists of two working conditions, namely 20Hz-0 (speed - load) and 30Hz-2V. The gear fault data collected include five types of gear operating states: healthy, peeling, broken tooth, crack, and wear:
2.2 Data Preprocessing
A sliding window is used to create the dataset, and the training set, validation set, and test set are uniformly divided into 7:2:1 ratios, finally saving the data. In this paper, the Markov transition field MTF is used as the method for time-frequency image transformation, and the generated time-frequency images are as follows:
3 Fault Diagnosis Model Based on PatchTF-WTNet
3.1 Define the Network Model
3.2 Set parameters and train the model
50 epochs, accuracy 100%, the PatchTF-WTNet network significantly improves classification results from fault signal features. It effectively extracts important features for model recognition, showing significant effects! Application demonstrates significant advantages. The PatchTF-WTNet unifies two complementary perspectives: "How does the original vibration impact occur" and "How do vibration states transfer", through wavelet convolution and bidirectional cross-patch attention to achieve deep multimodal collaborative diagnosis, representing a high-innovation multimodal fault diagnosis model for fault classification tasks.
3.3 Model Evaluation
(1) Accuracy, Precision, Recall, F1 Score
(2) Fault 5 Classification Confusion Matrix:
(3) Classification Label Visualization
(4) Original Data t-SNE Feature Visualization
(5) Post-Training t-SNE Feature Visualization:
Click to download: Full text data, Python code
Previously interesting content:
Python Bear Fault Diagnosis (19) Innovative Diagnosis Model Based on Transformer-BiLSTM
END
2. Friends who like this can click to follow, give the article a "like", share on WeChat Moments or discuss groups.

## Images

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
