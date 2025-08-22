# Procesamiento de Lenguaje Natural (NLP) - CEIA

**Autor:** Pedro Lucas Barrera  
**Carrera:** Carrera de Especialización en Inteligencia Artificial (CEIA)  
**Materia:** Procesamiento de Lenguaje Natural  

Este repositorio contiene todos los desafíos y trabajos prácticos desarrollados durante el curso de NLP de la CEIA. Cada notebook implementa diferentes técnicas y algoritmos fundamentales del procesamiento de lenguaje natural.

## 📁 Estructura del Repositorio

### 📊 Notebooks de Desafíos

#### `desafio1_pedro_barrera.ipynb`
**Tema:** Vectorización de Documentos y Clasificación con Naïve Bayes

**Descripción:**
Este notebook implementa técnicas de vectorización de texto y clasificación utilizando el dataset 20newsgroups. Se desarrollan tres puntos principales:

1. **Análisis de Similitud de Documentos:** Vectorización TF-IDF de documentos, selección aleatoria de 5 documentos y análisis de sus 5 más similares usando similitud coseno.

2. **Optimización de Clasificadores Naïve Bayes:** Entrenamiento y optimización de modelos MultinomialNB y ComplementNB, probando diferentes configuraciones de vectorizadores y hiperparámetros para maximizar el F1-score macro.

3. **Similitud entre Palabras:** Transposición de la matriz documento-término para obtener vectores de palabras y análisis de similitud semántica entre términos seleccionados manualmente.

**Resultados destacados:**
- Mejor configuración: ComplementNB con alpha=0.1 y vectorizador TF-IDF default (F1-score: 0.6954)
- Análisis detallado de similitudes entre palabras como 'computer', 'baseball', 'medical', 'religion' y 'car'

#### `desafio2_pedro_barrera.ipynb`
**Tema:** Word Embeddings con Gensim y Word2Vec

**Descripción:**
Implementación de word embeddings utilizando Gensim sobre un corpus personalizado de letras de canciones de Bob Dylan. El notebook incluye:

1. **Entrenamiento de Word2Vec:** Configuración y entrenamiento de un modelo Skip-gram con 300 dimensiones, ventana de contexto de 2 palabras y 20 negative samples.

2. **Análisis de Similitudes Semánticas:** Exploración de palabras similares para términos como "love", "night", "woman", "man", "truth" y "heart", analizando las relaciones semánticas capturadas por el modelo.

3. **Operaciones Vectoriales:** Pruebas de combinaciones de vectores (ej: woman + love + man) para explorar relaciones semánticas complejas.

4. **Visualización:** Mapas de calor de similitudes entre términos seleccionados y visualizaciones t-SNE en 2D y 3D de los embeddings.

**Resultados destacados:**
- Vocabulario de 948 palabras únicas del corpus de Bob Dylan
- Análisis de patrones poéticos y emocionales en las similitudes semánticas
- Visualizaciones interactivas de espacios de embeddings

#### `desafio3.ipynb`
**Tema:** Modelos de Lenguaje con Redes Neuronales Recurrentes

**Descripción:**
Este desafío explora el desarrollo de modelos de lenguaje utilizando capas LSTM para generar texto basándose en "La Metamorfosis" de Kafka. El notebook demuestra cómo los modelos pueden aprender patrones del lenguaje español:

1. **Preprocesamiento del Corpus:** Se trabaja con el texto completo de "La Metamorfosis", realizando limpieza, normalización de texto y análisis de distribución de longitudes de secuencias para determinar el contexto óptimo del modelo.

2. **Integración con FastText:** Se integran embeddings pre-entrenados de FastText en español (300 dimensiones). El modelo descarga automáticamente los embeddings si no están presentes, lo que mejora significativamente la representación semántica de las palabras.

3. **Arquitectura del Modelo:** Se diseña una red neuronal secuencial con:
   - Capa de Embedding usando FastText (congelada, no entrenable)
   - Dos capas LSTM de 64 unidades cada una con return_sequences=True
   - Capa de Dropout (0.2) para regularización
   - Capa Dense final con activación softmax para predicción de siguiente palabra

4. **Entrenamiento con Perplejidad:** Se implementa un callback personalizado (PplCallback) para monitorear la perplejidad durante el entrenamiento, incluyendo early stopping cuando la métrica no mejora por varias épocas consecutivas.

5. **Estrategias de Generación:** Se desarrollan diferentes técnicas de generación de texto:
   - Generación greedy (selección determinística)
   - Beam search determinístico
   - Beam search estocástico con control de temperatura
   - Interface interactiva con Gradio para experimentar en tiempo real

**Resultados obtenidos:**
- Modelo LSTM de dos capas (64 unidades cada una) entrenado durante 20 épocas
- Sistema de beam search configurable que permite controlar la creatividad vs coherencia
- Interface Gradio funcional para generar texto a partir de cualquier entrada
- Mejoras notables en la calidad del texto generado gracias a los embeddings FastText

**Observaciones:**
Aunque el modelo logra generar texto, produce secuencias que no tienen mucho sentido semántico. Esto es típico de los modelos de lenguaje más básicos y demuestra la complejidad real del procesamiento de lenguaje natural.

#### `desafio4_pedro_barrera.ipynb`
**Tema:** Chatbot QA con Arquitectura Encoder-Decoder y FastText Embeddings

**Descripción:**
Desarrollo de un chatbot conversacional usando el dataset ConvAI2 (Conversational Intelligence Challenge 2) con una arquitectura encoder-decoder basada en LSTM. Este desafío representa el proyecto más ambicioso de la materia, combinando múltiples técnicas avanzadas de NLP:

1. **Procesamiento del Dataset ConvAI2:** Descarga y preprocesamiento de 6,033 pares pregunta-respuesta extraídos de conversaciones reales en inglés, implementando limpieza de texto y tokenización especializada para diálogos.

2. **Integración de FastText Embeddings:** Implementación de una clase personalizada para cargar y manejar embeddings pre-entrenados FastText (cc.en.300.vec) de 1.6GB, optimizando el almacenamiento con serialización pickle para cargas futuras más rápidas.

3. **Arquitectura Encoder-Decoder Avanzada:** Diseño e implementación de un modelo seq2seq con:
   - Encoder LSTM (128 unidades) con embeddings FastText congelados
   - Decoder LSTM con embeddings entrenables
   - Tokens especiales `<sos>` y `<eos>` para control de secuencias
   - Arquitecturas separadas para entrenamiento e inferencia

4. **Sistema de Inferencia Conversacional:** Desarrollo de una función de respuesta que simula conversación real, procesando entrada del usuario y generando respuestas palabra por palabra usando los modelos encoder y decoder por separado.

**Resultados obtenidos:**
- Modelo entrenado por 40 épocas con accuracy de validación del 73% y entrenamiento del 81%
- Chatbot funcional capaz de responder preguntas básicas en inglés
- Sistema de embeddings optimizado que mejora significativamente la representación semántica

**Desafíos enfrentados:**
Como era de esperarse en un proyecto tan complejo, el modelo presenta algunas limitaciones típicas de chatbots seq2seq básicos: tendencia a generar respuestas repetitivas como "i like to go to the beach" o "i am a student". Esto refleja la naturaleza del dataset de entrenamiento y las limitaciones inherentes de los modelos encoder-decoder sin mecanismos de atención, una experiencia valiosa que demuestra tanto las posibilidades como los límites de estas arquitecturas.

### 📄 Archivos de Datos

#### `la_metamorfosis.txt`
Texto completo de "La Metamorfosis" de Franz Kafka en español, utilizado como corpus de referencia para el desafío 3.

#### `songs_dataset.zip`
Archivo comprimido que contiene el datasets con letras de canciones de distintos autores y bandas, uncluyendo el canciones de Bob Dylan (`bob-dylan.txt`) utilizado en el desafío 2 para entrenar el modelo Word2Vec. El corpus incluye una colección de letras de canciones que permite explorar las relaciones semánticas y patrones poéticos característicos del artista.

## 🚀 Instrucciones de Ejecución

### Prerrequisitos
```bash
# Instalar dependencias principales
pip install numpy pandas matplotlib seaborn scikit-learn
pip install tensorflow keras
pip install gensim
pip install gradio
pip install plotly
pip install scipy
pip install gdown  # Para descargas automáticas (Desafío 4)
```

### Ejecución de los Notebooks

1. **Para el Desafío 1:**
   ```bash
   jupyter notebook desafio1_pedro_barrera.ipynb
   ```
   - No requiere datasets externos (usa 20newsgroups de sklearn)

2. **Para el Desafío 2:**
   ```bash
   jupyter notebook desafio2_pedro_barrera.ipynb
   ```
   - Requiere el dataset `songs_dataset/bob-dylan.txt`, que se encuentra comprimido en el repo.

3. **Para el Desafío 3:**
   ```bash
   jupyter notebook desafio3.ipynb
   ```
   - Descarga automáticamente el dataset de canciones si no está presente
   - Tiempo estimado de entrenamiento: 30-45 minutos (dependiendo del hardware)
   - Incluye interface interactiva con Gradio

4. **Para el Desafío 4:**
   ```bash
   jupyter notebook desafio4_pedro_barrera.ipynb
   ```
   - Descarga automáticamente el dataset ConvAI2 (2.58MB) y los embeddings FastText (1.6GB)
   - **Tiempo estimado total: 1-2 horas** (incluyendo descarga de embeddings y entrenamiento)
   - Requiere conexión a internet para descargas automáticas
   - El modelo entrenado permite interacción conversacional básica

### Configuración del Entorno

```bash
# Clonar el repositorio
git clone [URL_del_repositorio]
cd NLP

# Crear entorno virtual (recomendado)
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

# Instalar dependencias
pip install -r requirements.txt  # Si existe
# O instalar manualmente las librerías listadas arriba
```

## 📈 Conceptos Implementados

### Técnicas de NLP Cubiertas:
-  Vectorización TF-IDF
-  Similitud Coseno
-  Tokenización
-  Clasificación con Naïve Bayes (Multinomial y Complement)
-  Word Embeddings (Word2Vec y FastText)
-  Modelos de Lenguaje con LSTM
-  Arquitecturas Encoder-Decoder (Seq2Seq)
-  Generación de Texto (Greedy, Beam Search)
-  Chatbots Conversacionales

## 📝 Licencia

Este material es parte del trabajo académico para la CEIA y está destinado únicamente a fines educativos. Sin embargo el contenido es libre para ser utilizado para cualquier fin que se desee

---

Para cualquier consulta o problema con la ejecución de los notebooks, revisar los comentarios dentro de cada archivo y si aun hay problemas no duden en contactarme :) 