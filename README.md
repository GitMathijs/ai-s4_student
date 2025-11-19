# Deep Learning (AI-S4)

[//]: # (HUGenerateStudentVersion=True)

(c) 2024 Hogeschool Utrecht  
Auteurs: David Isaacs Paternostro en Tijmen Muller

In deze repository staan algemene documenten voor semester 4 van AI, zoals 
templates, oefeningen en (code)voorbeelden.


## Conda environment

Als er nog geen [conda environment](
https://docs.conda.io/) genaamd `ai-s4` is, creëer deze dan door in de Anaconda
Prompt `conda` naar de directory van deze repository te gaan. Creëer vervolgens de omgeving met het volgende commando:

```bash
conda env create -f ai-s4_conda.yaml
```

Vervolgens moet je nog de juiste versie van PyTorch handmatig installeren, zie hiervoor de [instructies](#installatie-pytorch) hieronder.

### Interpreter instellen in VSCode

- Klik rechtsonder in de GUI waar je 'Python' ziet staan. Er komt midden bovenin je
   scherm een dropdown menu, kies daar: `ai-s4`.

### Interpreter instellen in PyCharm

1. Ga naar File >> Settings >> Project: _projectnaam_ >> Project Interpreter en dan:
   - kies `ai-s4` in het dropdown menu; of
   - ga naar Add Interpreter >> Add Local Interpreter >> Conda Environment >>
      Use Existing Environment >> selecteer `ai-s4` in het dropdown menu.
2. Klik rechtsonder in de GUI waar je 'Python' ziet staan.


## Installatie PyTorch 

Voor het maken en trainen van neurale netwerken maken we in dit semester gebruik van de library [PyTorch](https://pytorch.org/). 

De versie van PyTorch die
je moet installeren hangt af van of je gebruik kan en wil maken van je GPU om
je neurale netwerken op te trainen. Als je een configuratie hebt met een 
grafische kaart van NVidia is dit wel aan te raden, omdat het veel sneller gaat
dan trainen op je CPU. Je kan hier controleren of je GPU wordt ondersteund: 
https://developer.nvidia.com/cuda-gpus. Als je videokaart hebt die wordt ondersteund, dan moet je de CUDA Toolkit installeren om daar gebruik van te maken.

### CPU

De installatie van PyTorch zonder GPU support (en dus zonder CUDA) gaat als volgt:

```bash
pip3 install torch torchvision torchaudio torchmetrics --index-url https://download.pytorch.org/whl/cpu
```

Je kan controleren of de installatie is gelukt door `python` te starten in je terminal en
dan de volgende instructies uit te voeren:

```
Python 3.13.9 | packaged by conda-forge | (main, Oct 22 2025, 23:33:35) [GCC 14.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> torch.__version__
'2.9.0+cpu'
>>> torch.cuda.is_available()
False
```

### GPU (met CUDA)

Je installeert PyTorch met GPU support als volgt. Let op dat je hierbij de versie van CUDA selecteert die bij je videokaart past (hieronder wordt CUDA v12.8 geinstalleerd).

```bash
pip3 install torch torchvision torchaudio torchmetrics --index-url https://download.pytorch.org/whl/cu128
```

Je kan controleren of de installatie is gelukt door `python` te starten in je terminal en
dan de volgende instructies uit te voeren:

```
Python 3.13.9 | packaged by conda-forge | (main, Oct 22 2025, 23:33:35) [GCC 14.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
Ctrl click to launch VS Code Native REPL
>>> import torch
>>> torch.__version__
'2.9.0+cu128'
>>> torch.cuda.is_available()
True
>>> torch.cuda.get_device_name(0)
'NVIDIA RTX A1000 6GB Laptop GPU'
```

Let op! Als je PyTorch langs deze weg installeerd, zorg dan dat je updates en extra modules ook via `pip` installeert en _niet_ via `conda`!
