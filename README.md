# 🎯 Sistema de Reconhecimento Facial

Sistema de reconhecimento facial desenvolvido em Python utilizando as bibliotecas `face_recognition`, `OpenCV` e `dlib`. O projeto permite identificar rostos conhecidos em tempo real através da webcam ou em imagens estáticas.

![Python](https://img.shields.io/badge/Python-3.7%2B-blue)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green)
![Face Recognition](https://img.shields.io/badge/Face%20Recognition-1.3.0-orange)

---

## 📋 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades](#-funcionalidades)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Pré-requisitos](#-pré-requisitos)
- [Instalação](#-instalação)
- [Como Usar](#-como-usar)
- [Arquivos do Projeto](#-arquivos-do-projeto)
- [Como Funciona](#-como-funciona)
- [Adicionar Novos Rostos](#-adicionar-novos-rostos)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)

---

## 📖 Sobre o Projeto

Este projeto implementa um sistema de reconhecimento facial que utiliza técnicas de aprendizado de máquina para detectar e identificar rostos. O sistema compara rostos capturados em tempo real (via webcam) ou em imagens estáticas com um banco de dados de rostos conhecidos previamente cadastrados.

---

## ✨ Funcionalidades

- ✅ **Reconhecimento em tempo real** via webcam
- ✅ **Reconhecimento em imagens estáticas**
- ✅ **Identificação de múltiplos rostos** simultaneamente
- ✅ **Exibição do nome** da pessoa identificada na tela
- ✅ **Marcação visual** do rosto detectado com retângulo
- ✅ **Indicação de rostos desconhecidos**
- ✅ **Tolerância configurável** para comparação de rostos

---

## 📁 Estrutura do Projeto

```
reconhecimento-facial/
│
├── engine.py          # Módulo principal com funções de reconhecimento
├── face.py            # Script para reconhecimento via webcam em tempo real
├── fotos.py           # Script para reconhecimento em imagens estáticas
├── img/               # Pasta com imagens de rostos conhecidos
│   ├── bill-gates.webp
│   └── eu.jpeg
├── dlib-19.19/        # Biblioteca dlib (dependência do face_recognition)
├── dlib-19.19.zip     # Arquivo compactado do dlib
└── README.md          # Este arquivo
```

---

## 📦 Pré-requisitos

Antes de começar, você precisará ter instalado:

- **Python 3.7+**
- **Anaconda** (recomendado para gerenciamento de ambiente)
- **CMake**
- **Webcam** (para reconhecimento em tempo real)

---

## 🚀 Instalação



### Usando pip

```bash
pip install cmake
pip install dlib
pip install numpy
pip install opencv-python
pip install face-recognition
```

> ⚠️ **Nota:** A instalação do `dlib` pode exigir Visual Studio Build Tools no Windows.

---

## 💻 Como Usar

### Reconhecimento em Tempo Real (Webcam)

Execute o script `face.py` para iniciar o reconhecimento facial em tempo real:

```bash
python face.py
```

- O sistema irá abrir uma janela com a imagem da webcam
- Rostos conhecidos serão identificados e marcados com nome
- Rostos desconhecidos serão marcados como "desconhecido"
- Pressione **ESC** para encerrar o programa

### Reconhecimento em Imagem Estática

Execute o script `fotos.py` para reconhecer rostos em uma imagem:

```bash
python fotos.py
```

O resultado será exibido no terminal, indicando se o rosto foi reconhecido ou não.

---

## 📄 Arquivos do Projeto

### `engine.py`

Módulo principal contendo as funções essenciais:

| Função | Descrição |
|--------|-----------|
| `reconhece_rosto(url_imagem)` | Carrega uma imagem e extrai os pontos de encoding do rosto |
| `get_rosto()` | Retorna os rostos conhecidos e seus respectivos nomes |

### `face.py`

Script para reconhecimento facial em tempo real via webcam:

- Captura frames da webcam
- Detecta rostos usando o modelo HOG
- Compara com rostos conhecidos
- Desenha retângulos e exibe nomes na tela

### `fotos.py`

Script para reconhecimento em imagens estáticas:

- Carrega uma imagem de entrada
- Compara com o banco de rostos conhecidos
- Exibe resultado no terminal

---

## ⚙️ Como Funciona

1. **Carregamento de Rostos Conhecidos:**
   - As imagens dos rostos conhecidos são carregadas da pasta `img/`
   - O sistema extrai os "face encodings" (128 pontos de características) de cada rosto

2. **Detecção de Rostos:**
   - Utiliza o modelo HOG (Histogram of Oriented Gradients) para localizar rostos
   - Alternativamente, pode usar o modelo "large" para maior precisão

3. **Comparação:**
   - Compara os encodings do rosto detectado com os rostos conhecidos
   - Utiliza tolerância de 0.6 (padrão) para determinar correspondência
   - Calcula a distância facial para encontrar a melhor correspondência

4. **Exibição:**
   - Desenha um retângulo ao redor do rosto detectado
   - Exibe o nome da pessoa identificada ou "desconhecido"

---

## 👤 Adicionar Novos Rostos

Para adicionar um novo rosto ao sistema:

1. **Adicione a imagem** na pasta `img/`:
   ```
   img/nome-da-pessoa.jpg
   ```

2. **Edite o arquivo `engine.py`** na função `get_rosto()`:
   ```python
   rosto_conhecido = reconhece_rosto("./img/nome-da-pessoa.jpg")
   nomes_rostos.append("Nome da Pessoa")
   if(rosto_conhecido[0]):
       rostos_conhecidos.append(rosto_conhecido[1][0])
   ```

3. **Reinicie o sistema** para carregar o novo rosto.

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Versão | Descrição |
|------------|--------|-----------|
| **Python** | 3.7+ | Linguagem de programação |
| **face_recognition** | 1.3.0 | Biblioteca de reconhecimento facial |
| **OpenCV** | 4.x | Processamento de imagens e vídeo |
| **dlib** | 19.19 | Biblioteca de machine learning (base do face_recognition) |
| **NumPy** | 1.21.0 | Operações numéricas com arrays |

---

## 📝 Parâmetros Configuráveis

| Parâmetro | Local | Valor Padrão | Descrição |
|-----------|-------|--------------|-----------|
| `tolerance` | face.py | 0.6 | Tolerância para comparação (menor = mais restritivo) |
| `model` (detection) | face.py | 'hog' | Modelo de detecção ('hog' ou 'cnn') |
| `model` (encoding) | engine.py | 'large' | Modelo de encoding ('small' ou 'large') |

---

## ⚠️ Observações

- Certifique-se de ter boa iluminação para melhor detecção
- Imagens com rostos frontais funcionam melhor
- O modelo 'cnn' é mais preciso, mas requer GPU para bom desempenho
- O modelo 'hog' é mais rápido e funciona bem em CPU

