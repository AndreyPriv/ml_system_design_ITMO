# Machine Translation API (Russian-Mansi)

Этот проект реализует машинный перевод с русского на мансийский язык с использованием библиотеки `transformers` и модели Seq2Seq. API создано на базе FastAPI и упаковано в Docker-контейнер для удобства развертывания.

## Инференс API

Модель доступна через API по следующему адресу:

- **URL API**: [http://37.27.217.215:8000/translate](http://37.27.217.215:8000/translate)
- **Описание**: API принимает текст для перевода и возвращает переведенный текст.
- **Доступность**: API доступен через HTTPS.

## Доступные методы

### `POST /translate`
Перевод текста с одного языка на другой.

#### Параметры запроса

- **source_text** (string): Текст, который нужно перевести.
- **source_lang** (string): Язык исходного текста.
- **target_lang** (string): Язык, на который нужно перевести.

#### Пример запроса с использованием `curl`

Для отправки запроса к API используйте команду `curl`:

```bash
curl -X 'POST' \
  'http://37.27.217.215:8000/translate' \
  -H 'Content-Type: application/json' \
  -d '{
    "source_text": "Привет, как дела?",
    "source_lang": "ru",
    "target_lang": "en"
  }
```
Для удобного тестирования API через браузер, используйте интерфейс Swagger UI:

- **Ссылка на Swagger UI**: [http://37.27.217.215:8000/docs](http://37.27.217.215:8000/docs)

## Инструкция по использованию Swagger UI

1. Перейдите по ссылке [http://37.27.217.215/swagger](http://37.27.217.215:8000/docs).
2. На странице Swagger UI найдите метод **POST /translate**.
3. Введите текст для перевода, исходный и целевой языки в соответствующие поля.
4. Нажмите на кнопку **Try it out!**.
5. Результат перевода будет отображен ниже.

## Пример запроса

### Запрос

```json
{
  "source_text": "Привет, как дела?",
  "source_lang": "ru",
  "target_lang": "en"
}
```


## Структура проекта

- `app.py` — Основной файл FastAPI-приложения, содержащий логику для обработки запросов и перевода текста.
- `model/` — Директория, содержащая предобученную PyTorch модель (например, `pytorch_model.bin`).
- `requirements.txt` — Список зависимостей для проекта.
- `README.md` — Этот файл с инструкциями по установке и использованию.


### Видео демонстрация работы

[Посмотреть видео на Яндекс.Диске](https://disk.yandex.ru/i/xwFbzw74C2ZrCQ)

### Ссылка на модель
[Модель](https://drive.google.com/drive/folders/1WTjwXgYZ0hSjLzmdpoQ1eWM6TXOTbTar)
[Hugging Face](https://huggingface.co/Anzovi/nllb-rus-mansi-V2/tree/main)
## Установка и запуск

### 1. Локальная установка

1. 
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate  # Для Linux/macOS
   # .venv\Scripts\activate    # Для Windows
   pip install -r requirements.txt
   uvicorn app:app --reload

Приложение будет доступно по адресу: http://127.0.0.1:8000.


API
POST /translate
Этот эндпоинт принимает текст для перевода с исходного языка на целевой.

Пример запроса:
```bash
curl -X POST "http://127.0.0.1:8000/translate" \
-H "Content-Type: application/json" \
-d '{
    "text": "Пример текста для перевода",
    "src_lang": "rus_Cyrl",
    "tgt_lang": "mns_Cyrl"
}' 
```
```bash
Пример ответа:
{
  "translations": [
    "Мансийский перевод текста"
  ]
}
```




