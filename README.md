# JPEG-компрессор с нуля

Учебная реализация JPEG-подобного алгоритма сжатия изображений на Python. Лабораторная работа №2 по курсу «Алгоритмы и структуры данных» (ЛЭТИ).

## Описание

Компрессор реализует основные стадии алгоритма JPEG:

1. Перевод изображения из RGB в YCbCr
2. Даунсэмплинг цветностных каналов
3. Разбиение на блоки 8×8 и дискретное косинусное преобразование (ДКП)
4. Квантование с настраиваемым параметром качества (1–99)
5. Зигзаг-обход коэффициентов
6. Разностное кодирование DC и RLE для AC-коэффициентов (по ITU-T T.81)
7. Кодирование переменной длины и кодирование Хаффмана
8. Запись сжатых данных вместе с метаданными в файл и обратная декомпрессия

Задание лабораторной находится в [lab2.md](lab2.md).

## Установка

Требуется Python 3.10+.

```bash
git clone https://github.com/enlivee/AiSD_Lab2_JPG_compressor.git
cd AiSD_Lab2_JPG_compressor
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install pillow numpy matplotlib
```

## Запуск

Сжатие и декомпрессия из Python:

```python
from Task_2.compressor import compress_image, decompress_image

# сжатие: quality от 1 до 99
compress_image("input.jpg", "output.cmp", quality=50)

# декомпрессия
decompress_image("output.cmp", "restored.png")
```

Прогон на нескольких значениях качества:

```bash
python test_of_compress.py
```

Перед запуском укажите в `test_of_compress.py` путь к своему изображению в переменной `input_file`.
