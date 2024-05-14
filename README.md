# MACCS VS Morgan VS GCN

### Проект выполнил:
* Троценко Данил - ХИИ (ИТМО)
  
### Описание репозитория:
- *Dataset* - данные используемые в данном проекта
- *Scripts* - код проекта

## ___Описание:___ 
>Задача: Сравнить активно используемые представления молекул: Morgan fingerprints, MACCS fingerprints и графовое представление (GCN). Выяснить, какое представление является более репрезентативным для обучения нейронных сетей.

![Schematic-diagrams-of-several-molecular-fingerprints-a-Morgan-Morgan-fingerprints@1x_1](https://github.com/Da5ker/Fingerprints_VS_GCN/assets/113497168/2fec87c5-458d-483f-ba35-2b1497fa844b)

>Решение: для выполнения поставленной задачи был создан датасет из 10000 молекул в виде SMILES. Данные были разделены на train и test выборки (8000:2000). В качестве таргетной переменной выступал дескриптор LogP из библиотеки RDKit. Обучены полносвязная и графовая нейронные сети и сравнены по r2_score метрике и времени обучения.

>Вывод: Обучение нейронных сетей с помощью Morgan fingerprints происходит быстрее (**100 эпох: 160 сек vs 556 сек**), чем это происходит в GNN, но в этом примере надо брать во внимание, что архитектура GNN была сложнее (conv слои + dropout + meanpooling, ещё на 1 активацию больше), чем у FCNN. Обучение FCNN с Morgan FP показывает более лучший скор в короткой перспективе, но по мере увеличения количества эпох GCN обгоняет.

![image](https://github.com/Da5ker/Fingerprints_VS_GCN/assets/113497168/4f468186-2ff9-4ef1-9f72-22a3bcddcbfb)

