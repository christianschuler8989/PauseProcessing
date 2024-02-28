<a name="readme-top"></a>

<!-- PROJECT SHIELDS -->
<!--
*** We are using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/christianschuler8989/PauseProcessing">
    <img src="https://github.com/christianschuler8989/PauseProcessing-Slides-ESSV/blob/main/public/logo.png" alt="Logo" width="200" height="200">
  </a>

  <h3 align="center">Exploring the pauses in-between utterences.</h3>
  
  Preprocessing, Annotating and Experimenting Video Sequences of Pauses in-between Speech Segments
<!--
  <p align="center">
    <a href="https://github.com/christianschuler8989/PauseProcessing/tree/main/docs"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/christianschuler8989/PauseProcessing">View Demo (TODO)</a>
    ·
    <a href="https://github.com/christianschuler8989/PauseProcessing/issues">Report Bug</a>
    ·
    <a href="https://github.com/christianschuler8989/PauseProcessing/issues">Request Feature</a>
  </p>
-->
</div>



<p align="right">(<a href="#readme-top">back to top</a>)</p>

--- 

# Installation

* Clone this repository
```
git clone git@github.com:christianschuler8989/PauseProcessing.git
```

* Setup virtual environments and install the requirements
```
pip install -r requirements.txt
``` 



<p align="right">(<a href="#readme-top">back to top</a>)</p>

--- 

# Data Annotation Setup

## Preparing Video Material

### Identifying pauses

### Extract snippets (with and without padding)

### Extract items for annotation

### Potato (online/local) for easy workflow

#### Data preperation
```console
cd YOUR_PATH_HERE/PauseProcessing/potato/speaker_changes/data/
python potato_data_reader.py
```

#### Running a Potato Annotation Study
```console
python3 -m venv venvPotato
source venvPotato/bin/activate
pip3 install potato-annotation
cd YOUR_PATH_HERE/PauseProcessing/potato/

potato start ./speaker_changes/configs/postP_content.yaml
# → Annotation available in browser via localhost:8008

potato start ./speaker_changes/configs/preP_content.yaml
# → Annotation available in browser via localhost:8001
```

#### Processing annotation data
```console
cd YOUR_PATH_HERE/PauseProcessing/potato/speaker_changes/data/
python potato_annotation_reader.py
```







<p align="right">(<a href="#readme-top">back to top</a>)</p>

--- 

# Embeddings Creation

## Sentence Embeddings from Text
* Notebook: main_sent2vec.ipynb

### Sources
* [SBERT Docs for Computing Sentence Embeddings](https://www.sbert.net/examples/applications/computing-embeddings/README.html)
* [Cross English & German RoBERTa for Sentence Embeddings](https://huggingface.co/T-Systems-onsite/cross-en-de-roberta-sentence-transformer)

### Installation & Usage
* Create a conda environment
```console
conda create --name envRoBERTa
```

* Install the required packages
```console
conda install -n envRoBERTa conda-forge sentence-transformers protobuf ipywidgets
```

* Activate the conda environment and run the notebook cells
```console
source activate envRoBERTa
cd YOUR_PATH_HERE/PauseProcessing/source/main_sent2vec.ipynb
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

--- 

# Training and Evaluation





<p align="right">(<a href="#readme-top">back to top</a>)</p>

--- 

<!-- ACKNOWLEDGMENTS -->
# Acknowledgments

Helpful resources we would like to give credit to:

* [Potato: the POrtable Text Annotation TOol](https://github.com/davidjurgens/potato?tab=readme-ov-file)
* [py-webrtcvad, a python interface to the WebRTC Voice Activity Detector (VAD)](https://github.com/wiseman/py-webrtcvad)
* [Best-README-Template](https://github.com/othneildrew/Best-README-Template) 


<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/christianschuler8989/PauseProcessing.svg?style=for-the-badge
[contributors-url]: https://github.com/christianschuler8989/PauseProcessing/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/christianschuler8989/PauseProcessing.svg?style=for-the-badge
[forks-url]: https://github.com/christianschuler8989/PauseProcessing/network/members
[stars-shield]: https://img.shields.io/github/stars/christianschuler8989/PauseProcessing.svg?style=for-the-badge
[stars-url]: https://github.com/christianschuler8989/PauseProcessing/stargazers
[issues-shield]: https://img.shields.io/github/issues/christianschuler8989/PauseProcessing.svg?style=for-the-badge
[issues-url]: https://github.com/christianschuler8989/PauseProcessing/issues
[license-shield]: https://img.shields.io/github/license/christianschuler8989/PauseProcessing.svg?style=for-the-badge
[license-url]: https://github.com/christianschuler8989/PauseProcessing/blob/main/LICENSE


