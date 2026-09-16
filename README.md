# API de Predicción de Supervivencia del Titanic

Team Challenge final — Sprint 17 (despliegue de un modelo de Machine Learning como API REST).

Este proyecto expone un modelo de Random Forest que predice si un pasajero del Titanic habría sobrevivido, en función de su clase, sexo, edad y la tarifa pagada.

## 🚀 API en producción

La API está desplegada en Render y disponible en:

```
https://titanic-api-deploy.onrender.com
```

> ⚠️ El servidor gratuito de Render se "duerme" tras 14 minutos sin actividad. Si lleva un rato sin usarse, la primera petición puede tardar 40-60 segundos en responder mientras se reactiva.

## 📚 Documentación interactiva

FastAPI genera documentación automática. Podéis probar todos los endpoints directamente desde el navegador en:

```
https://titanic-api-deploy.onrender.com/docs
```

## 🧩 Endpoints disponibles

| Endpoint | Método | Descripción |
|---|---|---|
| `/` | GET | Mensaje de bienvenida con la lista de endpoints |
| `/predict` | POST | Predicción a partir de un JSON en el body |
| `/predict_get` | GET | Predicción a partir de parámetros en la URL |
| `/docs` | GET | Documentación interactiva (Swagger UI) |

### Parámetros de entrada

| Campo | Tipo | Descripción |
|---|---|---|
| `Pclass` | entero (1, 2 o 3) | Clase del billete |
| `Sex` | texto (`male` o `female`) | Sexo del pasajero |
| `Age` | número | Edad en años |
| `Fare` | número | Tarifa pagada |

### Ejemplo — POST `/predict`

**Petición:**
```json
{
  "Pclass": 1,
  "Sex": "female",
  "Age": 29,
  "Fare": 100
}
```

**Respuesta:**
```json
{
  "survived": 1,
  "probabilidad_supervivencia": 0.87
}
```

### Ejemplo — GET `/predict_get`

```
GET /predict_get?Pclass=3&Sex=male&Age=22&Fare=7.25
```

**Respuesta:**
```json
{
  "survived": 0,
  "probabilidad_supervivencia": 0.09
}
```

## 🖥️ Ejecutar en local

1. Instalar las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

2. Lanzar la API:
   ```bash
   uvicorn app:app --reload
   ```

3. Abrir en el navegador:
   ```
   http://127.0.0.1:8000/docs
   ```

## 🛠️ Entrenar el modelo de nuevo

Si se quiere reentrenar el modelo con datos nuevos, ejecutar:

```bash
python train_model.py
```

Esto generará un nuevo archivo `modelo_titanic.joblib` a partir de `titanic_train.csv`.

## 📦 Estructura del proyecto

```
├── app.py                  # API REST (FastAPI)
├── train_model.py          # Script de entrenamiento del modelo
├── modelo_titanic.joblib   # Modelo ya entrenado
├── titanic_train.csv       # Dataset de entrenamiento
├── requirements.txt        # Dependencias del proyecto
└── README.md
```

## 👥 Autores

- Hugo
- Carlos
