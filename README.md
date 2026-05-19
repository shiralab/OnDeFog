# OnDeFog
This repository contains the Pytorch implementation of [OnDeFog: Online Decision Transformer Under Frame Dropping]() by [Daiki Yotsufuji]().

If you use this code for your research, please cite us as:
```Bibtex
@InProceedings{10.1007/978-981-95-7072-0_41,
author="Yotsufuji, Daiki
and Nishihara, Kenta
and Shimizu, Shoma
and Uchida, Kento
and Shirakawa, Shinichi",
editor="Mei, Yi
and Qian, Chao
and Bai, Quan
and Xue, Bing
and Khanna, Sankalp",
title="OnDeFog: Online Decision Transformer Under Frame Dropping",
booktitle="PRICAI 2025: Trends in Artificial Intelligence",
year="2026",
publisher="Springer Nature Singapore",
address="Singapore",
pages="614--623",
abstract="In challenging real-world reinforcement learning applications, communication delays or sensor failures often cause frame dropping, in which the agent cannot receive the dropped states and associated rewards. To address the performance degradation caused by frame dropping, the Decision Transformer under Random Frame Dropping (DeFog) was developed by incorporating additional mechanisms into the decision transformer to tackle frame dropping. Although DeFog can mitigate performance degradation in frame-dropping environments, since DeFog is an offline learning method, it struggles to effectively generalize to novel states not adequately represented in the training dataset. In this study, we propose OnDeFog, which integrates the mechanisms in DeFog with the online decision transformer (ODT), an online reinforcement learning method that learns policies through direct environmental interaction. Comprehensive experimental evaluation demonstrates that our proposed OnDeFog achieves superior performance compared to ODT in environments characterized by high dropping frame rate and outperforms DeFog on datasets containing a large amount of low-reward data.",
isbn="978-981-95-7072-0"
}
```

## Requirements
```console
conda env create -f conda_env.yml
source activate ondefog
```

### Tips
If you encounter the `libstdc++.so.6: version 'GLIBCXX_3.4.xx' not found` error, the following command might help:
```console
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<path-to-your-conda-env>/lib
```
I have also found that `tensorboard` wants `protobuf` version to be `3.20.x`, and this helped
```console
# you might need to uninstall dm-control
pip3 install --upgrade protobuf==3.20.0
```


## Example
To train an ODT agent for `hopper` with the `medium-v2` dataset:
```console
python main.py
```
This will produce the `exp` folder, where all the outputs are going to be logged including tensorboard blobs. One can attach a tensorboard to monitor training by running:
```console
tensorboard --logdir exp
```

## License
The majority of `ondefog` is licensed under CC-BY-NC, however portions of the project are available under separate license terms:
* D4RL dataset -  Creative Commons Attribution 4.0 License (CC-BY)
* D4RL code, transformers, Lamb - Apache 2.0 License
* stable-baselines3, Gym, decision-transformer - MIT License

## Acknowledgements
This code was created based on [Online-dt](https://github.com/facebookresearch/online-dt) and [DeFog](https://github.com/hukz18/DeFog). I would like to thank the authors of those works.
