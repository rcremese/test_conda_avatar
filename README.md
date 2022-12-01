# Prise en main des librairies MONAI et Pytorch

## Initialisation de l'environnement
Afin de créer un environnement virtuel contenant toutes les dépendances, commencez par installer [mamba](https://mamba.readthedocs.io/en/latest/installation.html) (version améliorée de conda). Une fois installé, redémarez un terminal et lancez la ligne de commande suivante en remplaçant 'envname' par le nom que vous souhaitez donner à votre environement virtuel. 

`mamba env create -n envname -f config/environment.yml`

Si l'installation de toutes les dépendances ne fonctionne pas correctement, lancez la commande suivante. Et si ça ne fonctionne toujours pas, me contacter

`mamba env create -n envname -f config/env_from_history.yml`


Une fois toutes les dépendances installées, activez l'environnement virtuel que vous venez de créer, en remplaçant 'envname' par le nom que vous avez choisi pour votre environnement.

`mamba activate envname`

Enfin, vérifiez que Pytorch est bien connecté au GPU de votre machine en lançant la ligne commande suivante.  

`python -m "import torch; torch.cuda.is_available()"`

Si la réponse est False, vérifiez que le vous utilisez la bonne version de cuda avec la commande `nvidia-smi` et réinstaller manuellement [pytorch](https://pytorch.org/get-started/locally/).  

## Téléchargement des modèles et des données 
Si vous y avez accès, allez sur l'espace de partage du [Google Drive](https://drive.google.com/drive/folders/1y6mOUC0BpvcBmzK26wF7oTKslmqT0Tq0?usp=share_link) et téléchargez les données qui s'y trouvent. Placez dans le dossier models les fichiers :

- unet_3d-epoch=327-val_loss=0.069.zip 
- unet3d_spleen.onnx

Placez dans le dossier datas le fichier BTCV.zip (une fois qu'il sera disponible)

## Utilisation des notebooks
Assurez-vous que vous utilisez le bon kernel python pour faire tourner le notebook, il doit s'agir du noyau portant le nom de votre environnement virtuel !

Afin de vous faire la main, commencez par le notebook [spleen_segmentation_3d_lightning.ipynb](./spleen_segmentation_3d_lightning.ipynb) en veillant à modifier la variable **directory** dans la 3eme cellule de code par le chemin absolu du dossier dans lequel se trouve ce répertoire. Ce notebook permet d'avoir un apperçu des librairies pytorch-lightning et monai (surcouches de Pytorch) sur un problème de segmentation de râte à l'aide d'un modèle UNet 3D.

Si l'installation de l'environnement virtuel s'est bien passé, il n'est pas nécessaire d'exécuter la première cellule de code. Si vous le faites, l'interpréteur python va simplement s'assurer que vous avez toutes les librairies nécessaires. Si l'installation ne s'est pas bien passé, vous pouvez toujours créer un environnement vierge et exécuter la cellule en question afin d'installer toutes les dépendances nécessaires.

Afin de réduire le temps d'apprentissage du réseau, je vous ai fourni un modèle pré-entraînez ainsi que sont équivalent au format .onnx (cf. partie 2).

Enfin, si vous voulez un exemple plus impressionant des capacités de la librairie MONAI, vous pouvez essayer le deuxième notebook [swin_unetr_btcv_segmentation_3d.ipynb](./swin_unetr_btcv_segmentation_3d.ipynb) qui permet d'entraîner un réseau de neuronne plus performant (un transformer) sur une tâche de segmentation multi-classes contenant en toutes 13 organes présents dans l'abdomen. 

**Les données sont en cours d'acheminement sur le Drive.** 
