# hw1_digital_pathology

# Задача
Классифицировать гистологические изображения на 9 классов [ADI, BACK, DEB, LYM, MUC, MUS, NORM, STR, TUM].

# Описание решения
В работе использовалась предобученная модель DenseNet со 169 слоями, которая показывает наилучшие результаты при классификации клеточного фенотипа(https://www.hindawi.com/journals/cin/2022/6895833/), а также в задаче классификация белых кровяных телец(https://www.mdpi.com/1999-4893/16/11/525).

## Данные для обучения и тестирования модели

```python
DATASETS_LINKS = {
    'train': '1XtQzVQ5XbrfxpLHJuL0XBGJ5U7CS-cLi',
    'train_small': '1qd45xXfDwdZjktLFwQb-et-mAaFeCzOR',
    'train_tiny': '1I-2ZOuXLd4QwhZQQltp817Kn3J0Xgbui',
    'test': '1RfPou3pFKpuHDJZ-D9XDFzgvwpUBFlDr',
    'test_small': '1wbRsog0n7uGlHIPGLhyN-PMeT2kdQ2lI',
    'test_tiny': '1viiB0s041CNsAK4itvX8PnYthJ-MDnQc'
}
```

## Сохранение модели
```python
def save(self, name: str):
        self.model.save(f'{name}.h5')
```

## Загрузка модели
```python
def load(self, name: str):
        name_to_id_dict = {
            'best_last':'1-3Ov6JW87ho9Zfk7KKc5NeFgINLMfxHe',
            'best_small':'1-1vjd0EnRRTKug_ptDAyJhW_gDpJF6aA',
            'best_tiny':'1EEgqjrlZCfwU-f38867n0Gcst521ji-8'
        }
        link = f"https://drive.google.com/uc?export=download&id={name_to_id_dict.get(name, '')}"
        gdown.download(link, f'{name}.h5', quiet=False)
        self.model.load_weights(f'{name}.h5')
```

## Результаты
```python
10% of test: accuracy 0.9844
test: 0.9324
test-tiny: 0.9556
```
