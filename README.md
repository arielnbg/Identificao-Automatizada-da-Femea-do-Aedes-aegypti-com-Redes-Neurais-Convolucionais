# 🦟 Identificação Automatizada da Fêmea do *Aedes aegypti* com Redes Neurais Convolucionais

Este repositório contém a implementação e avaliação de **modelos de Deep Learning baseados em Redes Neurais Convolucionais (CNNs)** para a **identificação automática da fêmea do mosquito *Aedes aegypti***, vetor responsável pela transmissão da dengue.

O projeto foi desenvolvido como parte do **Trabalho de Conclusão de Curso (TCC)** do curso de **Bacharelado em Sistemas de Informação** da **Universidade de Pernambuco (UPE – Campus Caruaru)**, com foco em **Visão Computacional aplicada ao controle epidemiológico**.

---

## 🎯 Objetivo

Desenvolver e comparar modelos de **aprendizado profundo** capazes de classificar imagens de mosquitos *Aedes aegypti* em duas classes:

- **Macho**
- **Fêmea** (classe de interesse epidemiológico)

A correta identificação da fêmea é fundamental, pois **apenas ela transmite o vírus da dengue**, permitindo estratégias de controle vetorial mais eficientes e direcionadas.

---

## 🧠 Modelos Desenvolvidos

Foram implementados e avaliados **dois modelos principais**, ambos utilizando **Transfer Learning** com pesos pré-treinados no ImageNet.

### 🔹 Modelo CNN com MobileNetV2
- Arquitetura leve e eficiente
- Entrada: **224 × 224 × 3**
- Camadas adicionais:
  - GlobalAveragePooling2D
  - Dense (256 neurônios, ReLU)
  - Dropout (0.5)
  - Dense (Softmax)
- Fine-tuning aplicado nas camadas finais
- **Melhor desempenho geral**

### 🔹 Modelo CNN com VGG16
- Arquitetura profunda clássica
- Entrada: **150 × 150 × 3**
- Camadas adicionais:
  - Flatten
  - Dense (512 neurônios, ReLU)
  - Dropout (0.5)
  - Dense (Softmax)
- Camadas convolucionais congeladas

---

## 📊 Dataset

- **Total de imagens:** 2.000
- **Distribuição balanceada:**
  - 1.000 imagens de machos
  - 1.000 imagens de fêmeas
- **Aquisição das imagens:**
  - Microscopia digital (5 MP)
  - Diferentes ângulos e posicionamentos
- **Divisão dos dados:**
  - Treino: 70%
  - Validação: 15%
  - Teste: 15%

---

## 🔄 Pré-processamento e Data Augmentation

Aplicado principalmente ao conjunto de treino:

- Normalização dos pixels (1/255)
- Rotações aleatórias (±40°)
- Deslocamentos horizontais e verticais (20%)
- Zoom e cisalhamento
- Flip horizontal e vertical
- Ajuste de brilho (80% a 120%)

Essas técnicas aumentam a robustez dos modelos e reduzem overfitting.

---

## 📈 Métricas de Avaliação

Os modelos foram avaliados utilizando:

- Acurácia
- Precisão (Precision)
- Recall
- F1-Score
- Matriz de Confusão
- Curva ROC e AUC

---

## 🏆 Resultados

| Modelo        | Classe | Acurácia | Precisão | Recall | F1-Score |
|--------------|--------|----------|----------|--------|----------|
| VGG16        | Fêmea  | 0.89     | 0.90     | 0.87   | 0.89     |
| VGG16        | Macho  | 0.89     | 0.88     | 0.90   | 0.89     |
| MobileNetV2  | Fêmea  | 0.93     | 0.92     | 0.94   | 0.93     |
| MobileNetV2  | Macho  | 0.93     | 0.94     | 0.91   | 0.93     |

➡️ O modelo **MobileNetV2** apresentou desempenho superior, especialmente na identificação da classe **fêmea**, sendo escolhido como modelo final do projeto.

---

## ⚙️ Tecnologias Utilizadas

- Python 3.x
- TensorFlow / Keras
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn
- Google Colab

---

## 🚀 Como Executar

1. Abra os notebooks no **Google Colab**
2. Monte o Google Drive
3. Ajuste os caminhos do dataset
4. Execute o treinamento dos modelos
5. Avalie os resultados e salve o modelo treinado (`.h5`)

---

## 🔮 Trabalhos Futuros

- Avaliação com imagens em ambientes não controlados (campo)
- Implementação em dispositivos embarcados (edge computing)
- Testes com arquiteturas adicionais (EfficientNet, ResNet)
- Expansão para outras espécies de mosquitos

---

## 📚 Referência Acadêmica

GOMES, Ariel Nunes Braz.  
**Identificação Automatizada da Fêmea do *Aedes aegypti* com Redes Neurais Convolucionais: Uma Abordagem para o Controle Epidemiológico da Dengue.**  
Trabalho de Conclusão de Curso – Universidade de Pernambuco, 2024.
