# MACCS VS Morgan VS Graphs
Comparison of molecule representations (MACCS, Morgan fingerprints, Graphs)
  
## Описание репозитория:
- *Dataset* - данные используемые в данном проекта
- *Scripts* - скрипты

## ___Описание:___ 
>Задача: Сравнить распространённые представления молекул: Morgan fingerprints, MACCS fingerprints и графовое представление. Выяснить, какое представление является более репрезентативным для обучения нейронных сетей.

![Schematic-diagrams-of-several-molecular-fingerprints-a-Morgan-Morgan-fingerprints@1x_1](https://github.com/Da5ker/Fingerprints_VS_GCN/assets/113497168/2fec87c5-458d-483f-ba35-2b1497fa844b)

>Решение: для выполнения поставленной задачи был создан датасет из 10000 молекул в виде SMILES. Данные были разделены на train и test выборки (8000:2000). В качестве таргетной переменной выступал дескриптор LogP (коэффициент липофильности, сродство к органическим веществам) из библиотеки RDKit. Обучены полносвязные и графовая нейронные сети и сравнены по r2_score метрике и времени обучения.

>Вывод: __MACCS fingeprints__ показали себя как оптимальный инструмент кодировки молекул для быстрого обучения полносвязных нейронных сетей. __Графовое представление__ немного выигрывает в точности, чем MACCS (**100 эпох: 0.972 vs 0.969 (r2_score)**), но при этом GCN в 2.5-3 раза медленее обучается, чем FC c MACCS fingeprints (**100 эпох: 213 сек vs 600 сек**). В этом примере надо брать во внимание, что архитектура GNN была сложнее (conv слои + dropout + meanpooling, ещё на 1 активацию больше), чем у FCNN. __Morgan fingerprints__ значительно проигрывает по точности двум другим методам, в зависимости от заданного количества элементов в векторе (nBins) скорость обучения может варироваться, но при оптимальных значениях __Morgan fingerprints__ сильно сдают в скорости обучения.

![image](https://github.com/Da5ker/MACCS_vs_Morgan_GCN/assets/113497168/fa373148-141e-46a3-86b1-97c50984ed4b)


