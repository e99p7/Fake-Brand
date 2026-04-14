# Fake-Brand
Модель для распознавания оригинальных и фейковых товаров популярных модных брендов.

Fashion Brand Classification (Lightweight, Colab Version)

Данная версия оптимизирована для запуска в **Google Colab (free)** с ограниченными ресурсами.


Используемые технологии

* Apache Spark — обработка данных
* PyTorch — извлечение признаков (feature extraction)
* MobileNetV2 — облегчённая CNN модель
* Pandas UDF — интеграция Spark + Python

Особенности облегчённой версии

В отличие от полной версии:

* Используется **MobileNetV2** вместо тяжёлой InceptionV3
* Уменьшен размер изображений (128×128)
* Ограничен размер датасета
* Используется CPU вместо GPU (стабильность)

Это позволяет запускать проект в среде с ограниченными ресурсами.


Структура проекта

project/
│
├── Fake Brand Dataset.zip
├── fashion_data/
│   ├── Gucci/
│   ├── Nike/
│   ├── Adidas/
│   └── ...
│
├── main.ipynb
└── README.md

Установка (Colab)

pip install pyspark pandas pyarrow pillow torchvision


Запуск

1. Загрузите датасет в Colab:

Fake Brand Dataset.zip


2. Укажите пути:

zip_path = "/content/Fake Brand Dataset.zip"
extract_path = "/content/fashion_data"


3. Запустите все ячейки ноутбука

Pipeline

1. Распаковка ZIP-датасета
2. Создание Spark DataFrame
3. Ограничение объёма данных
4. Разделение на train/test
5. Извлечение признаков (MobileNetV2)
6. Кодирование меток
7. Обучение Logistic Regression
8. Предсказание
9. Оценка качества

Images → Spark DataFrame → MobileNetV2 (features) → Spark Vector → Logistic Regression → Prediction


Модель

Используется:

* MobileNetV2 (предобученная на ImageNet)
* Удалён последний слой классификации
* Извлекаются признаки (1280-dimensional embeddings)

Далее:

* обучается Logistic Regression (Spark ML)


Метрика

Используется:

* Accuracy (MulticlassClassificationEvaluator)


Ограничения

* Используется только часть датасета (~500 изображений)
* Снижено качество модели по сравнению с полной версией
* CPU вместо GPU увеличивает время выполнения


Причина упрощения

Полная версия проекта (InceptionV3 + GPU + Spark) требует значительных вычислительных ресурсов и может не запускаться в Google Colab (free).

Поэтому была использована облегчённая архитектура MobileNetV2, обеспечивающая аналогичный процесс transfer learning при меньших затратах ресурсов.


Возможные улучшения

* Использование GPU
* Возврат к InceptionV3
* Увеличение размера датасета
* Fine-tuning модели
* Добавление MLflow
* Развёртывание API (FastAPI)

