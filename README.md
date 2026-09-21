# 🧠 MLP: NumPy to PyTorch

### Image classification with a multilayer perceptron implemented from scratch and in PyTorch

[English](#english) · [Русский](#русский)

---

## English

### Overview

This project explores the internals of a multilayer perceptron (MLP) by implementing the model in two ways:

1. **from scratch with NumPy**
2. **with PyTorch**

The models are trained for multiclass image classification on QuickDraw-style bitmap drawings. The project covers the complete workflow from preprocessing and manual backpropagation to model evaluation and error analysis.

### What is implemented

- exploratory analysis and image preprocessing
- train / validation / test split
- custom NumPy MLP
- forward and backward propagation
- softmax cross-entropy loss
- numerical gradient checking
- PyTorch `Dataset` and `DataLoader`
- equivalent MLP implemented with `torch.nn`
- model checkpointing using validation accuracy
- comparison of NumPy and PyTorch implementations
- ReLU vs Tanh experiment
- inference and qualitative error analysis

### Results

| Implementation | Validation accuracy | Test accuracy | Best epoch |
|---|---:|---:|---:|
| NumPy MLP | **40.60%** | **40.66%** | 16 |
| PyTorch MLP | **40.43%** | **40.50%** | 15 |

In the saved run, the NumPy implementation required about **1013.54 s** of training time, while the PyTorch implementation required about **591.36 s**.

The notebook also shows that both implementations exceeded the project target of **40% accuracy** on validation and test data.

### Error analysis

The models tend to confuse drawings with similar shapes and very simplified or ambiguous sketches. This is expected for a fully connected MLP because spatial image structure is flattened into a vector of pixels.

The validation curves also show signs of overfitting after the best epoch, so the final evaluation uses the checkpoint with the highest validation accuracy.

### Repository structure

```text
mlp-numpy-to-pytorch/
├── notebook.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

The dataset and trained model artifacts are intentionally not included in the repository.

### Run

```bash
pip install -r requirements.txt
```

Open `notebook.ipynb` in Jupyter Notebook or Google Colab and run the cells in order. The original QuickDraw data archive is required to reproduce training from scratch.

---

## Русский

### О проекте

Проект показывает устройство многослойного перцептрона не только через высокоуровневый фреймворк, но и через собственную реализацию основных операций.

Одна модель реализована **с нуля на NumPy**, вторая построена на **PyTorch**. Обе решают задачу многоклассовой классификации bitmap-рисунков QuickDraw.

### Что реализовано

- исследование и подготовка данных
- разбиение на train / validation / test
- собственный MLP на NumPy
- прямое и обратное распространение
- softmax и cross-entropy
- численная проверка градиентов
- `Dataset` и `DataLoader` в PyTorch
- аналогичная архитектура на `torch.nn`
- сохранение лучшей модели по validation accuracy
- сравнение NumPy и PyTorch
- эксперимент ReLU vs Tanh
- инференс и анализ ошибок

### Результаты

| Реализация | Validation accuracy | Test accuracy | Лучшая эпоха |
|---|---:|---:|---:|
| NumPy MLP | **40.60%** | **40.66%** | 16 |
| PyTorch MLP | **40.43%** | **40.50%** | 15 |

В сохранённом запуске обучение NumPy-модели заняло около **1013.54 с**, PyTorch-модели около **591.36 с**.

Обе реализации преодолели целевой порог проекта в **40% accuracy** на validation и test.

### Анализ ошибок

Наиболее сложными оказываются визуально похожие классы, а также слишком упрощённые и неоднозначные рисунки. MLP получает изображение как плоский вектор пикселей, поэтому не использует пространственную структуру изображения так эффективно, как свёрточные архитектуры.

После лучшей эпохи validation accuracy начинает ухудшаться, что указывает на переобучение. Поэтому для итоговой оценки используются сохранённые состояния моделей с лучшим validation accuracy.

### Запуск

```bash
pip install -r requirements.txt
```

После установки зависимостей откройте `notebook.ipynb` в Jupyter Notebook или Google Colab. Для полного воспроизведения обучения потребуется исходный архив с данными QuickDraw.
