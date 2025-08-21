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
Desarrollo de un modelo de lenguaje basado en LSTM para generación de texto usando letras de canciones de The Beatles. El notebook cubre:

1. **Preprocesamiento y Tokenización:** Análisis de distribución de longitudes de secuencias, tokenización con Keras y estructuración del dataset many-to-many.

2. **Arquitectura del Modelo:** Red neuronal con capas de Embedding, LSTM bidireccional y Dense con activación softmax para predicción de siguiente palabra.

3. **Entrenamiento con Perplejidad:** Implementación de callback personalizado para monitorear la perplejidad como métrica de calidad del modelo de lenguaje.

4. **Estrategias de Generación:** Implementación de diferentes técnicas de generación:
   - Greedy search (selección determinística)
   - Beam search determinístico
   - Beam search estocástico con temperatura

**Resultados destacados:**
- Modelo con arquitectura LSTM de 100 unidades en dos capas
- Sistema de generación con beam search configurable
- Interface interactiva con Gradio para pruebas del modelo

### 📄 Archivos de Datos

#### `la_metamorfosis.txt`
Texto completo de "La Metamorfosis" de Franz Kafka en español, utilizado como corpus de referencia para algunos ejercicios y experimentos adicionales.

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
```

### Ejecución de los Notebooks

1. **Para el Desafío 1:**
   ```bash
   jupyter notebook desafio1_pedro_barrera.ipynb
   ```
   - No requiere datasets externos (usa 20newsgroups de sklearn)
   - Tiempo estimado de ejecución: 15-20 minutos

2. **Para el Desafío 2:**
   ```bash
   jupyter notebook desafio2_pedro_barrera.ipynb
   ```
   - Requiere el dataset `datasets/songs_dataset/bob-dylan.txt`
   - Tiempo estimado de ejecución: 10-15 minutos

3. **Para el Desafío 3:**
   ```bash
   jupyter notebook desafio3.ipynb
   ```
   - Descarga automáticamente el dataset de canciones si no está presente
   - Tiempo estimado de entrenamiento: 30-45 minutos (dependiendo del hardware)
   - Incluye interface interactiva con Gradio

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
- ✅ Vectorización TF-IDF
- ✅ Similitud Coseno
- ✅ Clasificación con Naïve Bayes (Multinomial y Complement)
- ✅ Word Embeddings (Word2Vec)
- ✅ Modelos de Lenguaje con LSTM
- ✅ Generación de Texto (Greedy, Beam Search)
- ✅ Métricas de Evaluación (F1-score, Perplejidad)

### Visualizaciones:
- ✅ Mapas de calor de similitudes
- ✅ Distribuciones de longitudes de secuencias
- ✅ Evolución de métricas durante entrenamiento
- ✅ Proyecciones t-SNE de embeddings
- ✅ Interfaces interactivas con Gradio

## 📚 Estructura de Aprendizaje

Cada desafío está diseñado para construir sobre los conceptos anteriores:

1. **Desafío 1** → Fundamentos de vectorización y clasificación
2. **Desafío 2** → Representaciones densas y similitud semántica
3. **Desafío 3** → Modelos generativos y arquitecturas profundas

## 🔧 Notas Técnicas

- Los notebooks incluyen análisis detallados de resultados y conclusiones
- Se utilizan técnicas de reproducibilidad (semillas aleatorias)
- El código está documentado y comentado en español
- Se incluyen callbacks personalizados para monitoreo de entrenamiento
- Las visualizaciones son interactivas cuando es posible

## 📝 Licencia

Este material es parte del trabajo académico para la CEIA y está destinado únicamente a fines educativos.

---

Para cualquier consulta o problema con la ejecución de los notebooks, revisar los comentarios dentro de cada archivo o contactar al autor. 