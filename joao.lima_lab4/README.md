# Laboratório 4 – Segmentação Semântica com U-Net

**Instituto Tecnológico de Aeronáutica – ITA**
**Disciplina:** Aprendizado Profundo – CM-204
**Professores:** Marcos Ricardo Omena de Albuquerque Maximo · André Oliveira Françani

---

## Descrição

Implementação da arquitetura **U-Net** com **PyTorch** para **segmentação semântica** de imagens aéreas de Dubai, do dataset [Semantic Segmentation of Aerial Imagery (Kaggle)](https://www.kaggle.com/datasets/humansintheloop/semantic-segmentation-of-aerial-imagery). A rede classifica cada pixel da imagem em uma de 6 classes.

---

## Classes de Segmentação

| Classe       | Cor (HEX) | Rótulo |
|--------------|-----------|:------:|
| Building     | `#3C1098` | 0      |
| Land         | `#8429F6` | 1      |
| Road         | `#6EC1E4` | 2      |
| Vegetation   | `#FEDD3A` | 3      |
| Water        | `#E2A929` | 4      |
| Unlabeled    | `#9B9B9B` | 5      |

---

## Arquitetura – U-Net

A U-Net possui formato de "U" com dois caminhos:

- **Encoder** (contração): blocos convolucionais + MaxPooling, duplicando os canais a cada nível (64 → 128 → 256 → 512 → 1024)
- **Decoder** (expansão): ConvTranspose2d + concatenação com skip connections, reduzindo os canais pela metade a cada nível
- **Saída**: camada convolucional com 6 canais (uma por classe)

**Total de parâmetros treináveis:** 31.032.070

---

## Configuração do Treinamento

| Parâmetro        | Valor                         |
|------------------|-------------------------------|
| Épocas           | 80                            |
| Otimizador       | Adam                          |
| Função de perda  | Categorical CrossEntropy      |
| Melhor época     | 29 (menor loss de validação)  |
| Resolução        | 256 × 256 px                  |
| Divisão dos dados| Treino / Validação / Teste    |

> O treinamento demora várias horas em GPU. Os pesos pré-treinados são fornecidos e carregados automaticamente.

---

## Tarefas

| Seção | Tarefa |
|-------|--------|
| 4.1   | Leitura e pré-processamento das imagens (decodificação RGB → label) |
| 4.2   | Implementação da arquitetura U-Net |
| 4.3   | Visualização dos resultados de segmentação no conjunto de teste |
| 4.4   | Treinamento da rede (opcional — pesos pré-treinados fornecidos) |

---

## Estrutura do Projeto

```
joao.lima_lab4/
├── cm204_lab4.ipynb        # Notebook principal
├── joao_lima_lab3.pdf      # Relatório
└── data/                   # Imagens aéreas de Dubai (256×256)
```

---

## Como Executar

### Pré-requisitos

```bash
pip install torch torchvision numpy matplotlib
```

### Execução

Abra e execute o notebook `cm204_lab4.ipynb` em ordem:

1. **Célula download** – Baixa as imagens e os pesos pré-treinados da U-Net
2. **Seção 4.1** – Leitura e pré-processamento dos dados
3. **Seção 4.2** – Implementação da U-Net e carregamento dos pesos
4. **Seção 4.3** – Predição e visualização da segmentação nas imagens de teste
5. **Seção 4.4** *(opcional)* – Treinamento completo da rede

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JoaoVitorCoelhoG/Aprendizado-Profundo/blob/main/cm204_lab4.ipynb)

---

## Entrega

Arquivo: `joao.lima_lab4.zip` contendo o notebook `.ipynb` e o relatório `.pdf`.
