# Laboratório 3 – Redes Neurais Convolucionais

**Instituto Tecnológico de Aeronáutica – ITA**
**Disciplina:** Aprendizado Profundo – CM-204
**Professor:** Marcos Ricardo Omena de Albuquerque Maximo

---

## Descrição

Implementação, treinamento e avaliação da rede neural convolucional **LeNet-5** no dataset **MNIST**, reproduzindo o trabalho clássico de Yann LeCun.

O MNIST contém imagens em escala de cinza (28×28 px) de dígitos decimais escritos à mão (0–9), com 60.000 imagens de treino e 10.000 de teste.

---

## Arquitetura – LeNet-5

| Camada | Tipo              | Filtros | Saída       | Kernel | Stride | Ativação |
|--------|-------------------|---------|-------------|--------|--------|----------|
| 1      | Convolução        | 6       | 28×28×6     | 5×5    | 1      | Tanh     |
| 2      | Average Pooling   | —       | 14×14×6     | 2×2    | 2      | —        |
| 3      | Convolução        | 16      | 10×10×16    | 5×5    | 1      | Tanh     |
| 4      | Average Pooling   | —       | 5×5×16      | 2×2    | 2      | —        |
| 5      | Flatten           | —       | 400         | —      | —      | —        |
| 6      | Fully Connected   | —       | 120         | —      | —      | Tanh     |
| 7      | Fully Connected   | —       | 84          | —      | —      | Tanh     |
| 8      | Fully Connected   | —       | 10          | —      | —      | Softmax  |

> As imagens MNIST (28×28) são padded para 32×32 antes de entrar na rede.

---

## Configuração do Treinamento

| Parâmetro        | Valor            |
|------------------|------------------|
| Épocas           | 20               |
| Batch size       | 128              |
| Otimizador       | Adam (lr=2e-4)   |
| Função de perda  | CrossEntropyLoss |
| Dispositivo      | CUDA / MPS / CPU |

---

## Estrutura do Projeto

```
joao.lima_lab3/
├── cm204_lab3.ipynb       # Notebook principal
├── joao_lima_lab3.pdf     # Relatório
├── lenet5.pth             # Pesos treinados do modelo
├── data/
│   └── MNIST/             # Dataset baixado automaticamente
├── lenet5/                # Arquivos auxiliares do modelo
└── results/
    ├── loss.png            # Curvas de loss (treino e teste)
    ├── accuracy.png        # Curvas de acurácia (treino e teste)
    └── *.png               # Imagens de teste e classificações erradas
```

---

## Como Executar

### Pré-requisitos

```bash
pip install torch torchvision torchinfo tqdm matplotlib
```

### Execução

Abra e execute o notebook `cm204_lab3.ipynb` em ordem:

1. **Célula 4.1** – Download automático do MNIST
2. **Célula 4.2** – Exploração do dataset
3. **Célula 4.3** – Definição da arquitetura LeNet-5
4. **Célula 4.4** – Treinamento (salva pesos em `lenet5.pth`)
5. **Célula 4.5** – Avaliação e visualização dos resultados

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JoaoVitorCoelhoG/-Bot-de-Atendimento-WhatsApp/blob/main/cm204_lab3.ipynb)

---

## Resultados

Os gráficos de **loss** e **acurácia** ao longo das épocas são salvos em `results/`. O modelo treinado atinge alta acurácia no conjunto de teste, consistente com o desempenho original da LeNet-5 reportado na literatura (~99%).

---

## Entrega

Arquivo: `joao.lima_lab3.zip` contendo o notebook `.ipynb` e o relatório `.pdf`.
