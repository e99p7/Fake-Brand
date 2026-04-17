
**Fake-Brand Detection (AI)**

A machine learning model for detecting counterfeit fashion products (fake vs genuine) from images.

The project is designed to work under limited resources (Google Colab free) while applying modern computer vision techniques.

---

**Project Versions**

This repository contains two versions:

**Baseline (Lightweight, Spark)**

* Apache Spark + Logistic Regression
* Feature extraction using MobileNetV2
* Designed for CPU and scalable pipelines


**Production Version (Recommended)**

* PyTorch + EfficientNet-B0
* Transfer learning + fine-tuning
* Binary classification (fake vs genuine)
* Test-Time Augmentation (TTA)
* Threshold tuning
* Early stopping

---

**Results (Production)**

* Accuracy: **0.79**
* F1-score:

  * genuine: 0.80
  * fake: 0.78
* Balanced performance with minimal overfitting

---

**Tech Stack**

Core:

* Python
* PyTorch
* torchvision
* scikit-learn

**ML / CV:**

* EfficientNet-B0 (ImageNet pretrained)
* Transfer Learning
* Fine-tuning
* Data Augmentation
* Class weighting
* Threshold tuning
* Test-Time Augmentation (TTA)

**Baseline:**

* Apache Spark
* Pandas UDF
* Logistic Regression

---

**Pipeline (Production)**

```
Images → Augmentation → EfficientNet → Fine-tuning → Threshold tuning → Prediction
```

---

**Pipeline (Baseline)**

```
Images → Spark DataFrame → MobileNetV2 → Logistic Regression → Prediction
```

---

**Dataset**

* Fake Brand Dataset (Kaggle)
* Limited to ~500 images (Colab constraint)
* Stratified sampling applied

---

**Model Architecture**

* Backbone: EfficientNet-B0
* Classifier: Fully connected layer + dropout
* Task: binary classification (fake vs genuine)



---

**Installation**

```
pip install torch torchvision pillow scikit-learn
```

---

**How to Run**

1. Download dataset:
   https://www.kaggle.com/datasets/prashanthgolla/fake-brand-data

2. Upload to Colab

3. Run notebook

---

**Limitations**

* Small dataset (~500 images)
* High variability of images
* No explicit ROI/logo detection

---

**Future Improvements**

* Larger dataset
* Hard example mining
* Logo/ROI detection
* Model ensemble
* ONNX optimization
* FastAPI deployment

---

**Summary**

This project demonstrates a production-style ML pipeline:

* data processing
* model training
* optimization
* deployment readiness

---



**Fake-Brand Detection (AI)**

Модель машинного обучения для распознавания оригинальных и фейковых товаров популярных модных брендов.

Проект реализован с учётом ограниченных ресурсов (Google Colab free), но использует современные подходы компьютерного зрения и transfer learning.

---

**Версия проекта**

В репозитории представлены две версии:

**Базовая (Lightweight, Spark)**

* Apache Spark + Logistic Regression
* Feature extraction через MobileNetV2
* Подходит для CPU и больших пайплайнов обработки данных

**Production-версия (рекомендуется)**

* PyTorch + EfficientNet-B0
* Fine-tuning нейросети
* Binary classification (fake vs genuine)
* Test-Time Augmentation (TTA)
* Threshold tuning
* Early stopping

---

**Результаты (Production версия)**

* Accuracy: **0.79**
* F1-score:

  * genuine: 0.80
  * fake: 0.78
* Сбалансированные метрики без сильного переобучения

---

**Используемые технологии**

Core:

* Python
* PyTorch
* torchvision
* scikit-learn

**ML / CV:**

* EfficientNet-B0 (ImageNet pretrained)
* Transfer Learning
* Fine-tuning
* Data Augmentation
* Class weighting
* Threshold tuning
* Test-Time Augmentation (TTA)

**Базовая версия:**

* Apache Spark
* Pandas UDF
* Logistic Regression

---

**Pipeline (Production)**

```
Images → Augmentation → EfficientNet → Fine-tuning → Threshold tuning → Prediction
```

---

**Pipeline (Baseline Spark)**

```
Images → Spark DataFrame → MobileNetV2 (features) → Spark Vector → Logistic Regression → Prediction
```

---

**Данные**

* Датасет: Fake Brand Dataset (Kaggle)
* Ограничение: ~500 изображений (Colab free)
* Используется стратифицированная выборка

---

**Архитектура модели**

Production версия:

* Backbone: EfficientNet-B0
* Классификатор: Fully Connected + Dropout
* Задача: бинарная классификация (fake / genuine)


---

**Установка (Colab)**

```
pip install torch torchvision pillow scikit-learn
```

---

**Запуск**

1. Скачать датасет:
   https://www.kaggle.com/datasets/prashanthgolla/fake-brand-data

2. Загрузить в Colab

3. Запустить ноутбук

---

**Ограничения**

* Малый размер датасета (~500 изображений)
* Высокая вариативность изображений
* Отсутствие детекции ROI (логотипов)

---

**Возможные улучшения**

* Увеличение датасета
* Hard Example Mining
* Детекция логотипов (ROI)
* Ensemble моделей
* ONNX оптимизация
* Развёртывание через FastAPI

---

**Итог**

Проект демонстрирует полный ML pipeline:

* обработка данных
* обучение модели
* оптимизация
* подготовка к продакшену

Даже при ограниченных ресурсах достигается стабильное качество.

---


