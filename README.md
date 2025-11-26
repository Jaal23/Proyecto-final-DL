# 🧬 Clasificación Taxonómica de Proteínas con Deep Learning


📖 Descripción General
Este proyecto explora y compara diferentes arquitecturas de Deep Learning para resolver un problema fundamental en la bioinformática: predecir el origen taxonómico (especie) de una proteína basándose únicamente en su secuencia primaria de aminoácidos.
El estudio se centra en el desafío de modelar datos secuenciales biológicos de longitud variable, contrastando enfoques de Visión Artificial (CNN) contra enfoques de Procesamiento de Lenguaje Natural (RNN y Transformers).
El proyecto utiliza un subconjunto del dataset del desafío CAFA 6 Protein Function Prediction.
🎯 Objetivos del Proyecto
 * Comparación de Arquitecturas: Evaluar el rendimiento de modelos convolucionales (ResNet) versus modelos secuenciales (GRU, LSTM, Transformer) en datos biológicos.
 * Ingeniería de Características: Implementar técnicas de Embedding aprendible frente a codificación One-Hot y proyecciones espaciales.
 * Robustez Metodológica: Identificar y solucionar problemas de Fuga de Datos (Data Leakage) mediante estrategias de split estratificado.
📂 Dataset y Preprocesamiento
Los datos provienen de secuencias curadas de UniProtKB (Swiss-Prot).
 * Entrada (X): Secuencias de aminoácidos (Archivos FASTA).
 * Salida (Y): Identificadores de Taxón (Archivos TSV).

El repositorio contiene la implementación de tres paradigmas distintos:
1. 🏎 Turbo GRU 
 * Tipo: Red Neuronal Recurrente.
 * Arquitectura: Capa de Embedding + GRU Bidireccional + Dropout.
 * Justificación: Captura dependencias secuenciales de largo alcance y el contexto global (N-terminal \leftrightarrow C-terminal) de manera eficiente.
 * Archivo: Turbo_GRU.py
2. 🤖 Transformer "From Scratch" 
 * Tipo: Mecanismo de Atención.
 * Arquitectura: Positional Embedding + Multi-Head Attention + Feed Forward Network.
 * Optimizador: AdamW con Cosine Decay Scheduler.
 * Justificación: Permite modelar interacciones entre aminoácidos distantes sin las limitaciones de memoria de las RNNs.
 * Archivo: Transformer_Genomica.py
3. 🖼 ResNet-50 (Línea Base Experimental)
 * Tipo: Red Neuronal Convolucional (CNN).
 * Metodología: Adaptación forzada de secuencias 1D a "Pseudo-Imágenes" 3D.
 * Resultado: Se utilizó para demostrar que los enfoques de visión pura no son ideales para datos secuenciales biológicos sin representaciones espaciales reales.
 * Archivo: ResNet_Genomica.py

 * Implementación de Transfer Learning utilizando LLMs biológicos pre-entrenados como ProtBERT o ESM-2 para superar la barrera del 50% de precisión.
 * Expansión del dataset para incluir más clases taxonómicas.
Autor: Javier Alejandro Martínez Labra
