# Laboratório 1 – Descida de Gradiente e Introdução ao PyTorch

**Instituto Tecnológico de Aeronáutica – ITA**
**Disciplina:** Aprendizado Profundo – CM-204
**Professor:** Marcos Ricardo Omena de Albuquerque Maximo

---

## Descrição

Implementação do algoritmo de **Descida de Gradiente** (Gradient Descent) usando **NumPy** puro e **PyTorch**, aplicado a um problema de regressão linear para determinação de parâmetros físicos do movimento de uma bola em um campo de futebol de robôs (VSS – Very Small Size).

O problema é um *toy problem*: a solução analítica via **Método dos Mínimos Quadrados (MMQ)** é conhecida e serve como referência para validar as implementações.

---

## Problema

Determinar o **coeficiente de desaceleração** (*rolling friction*) de uma bola em movimento no campo de futebol de robôs da ITAndroids. Os dados (posição × tempo) foram coletados em competição real por Thiago Filipe de Medeiros (COMP-19).

---

## Tarefas Implementadas

| Seção | Tarefa |
|-------|--------|
| 4.1   | Tutorial de NumPy (vetores, matrizes, operações) |
| 4.2   | Tutorial de PyTorch (tensores, autograd, `backward()`) |
| 4.3   | Implementação de `gradient_descent_numpy()` |
| 4.4   | Implementação de `gradient_descent_torch()` |
| 4.5   | Comparação dos métodos (NumPy, PyTorch, MMQ) |

### Algoritmo de Descida de Gradiente

$$\boldsymbol{\theta}_{k+1} = \boldsymbol{\theta}_k - \alpha \left. \frac{\partial J}{\partial \boldsymbol{\theta}} \right|_{\boldsymbol{\theta}_k}$$

**Condições de parada:** custo $J(\theta) < \epsilon$ ou número máximo de iterações atingido.

---

## Estrutura do Projeto

```
joao.lima_lab1/
├── joao.lima_lab1.ipynb      # Notebook principal
├── joao.lima_lab1.pdf        # Relatório
└── cm204_lab1_data/
    ├── data.txt              # Dados reais de posição da bola (VSS)
    ├── least_squares.py      # Implementação do MMQ (referência)
    └── results/              # Gráficos gerados
```

---

## Como Executar

### Pré-requisitos

```bash
pip install torch numpy matplotlib
```

### Execução

Abra e execute o notebook `joao.lima_lab1.ipynb` em ordem:

1. **Célula download** – Baixa os dados (`data.txt`)
2. **Seção 4.1** – Tutorial NumPy (opcional, sem saída para correção)
3. **Seção 4.2** – Tutorial PyTorch (opcional, sem saída para correção)
4. **Seção 4.3** – Implementação e teste do GD com NumPy
5. **Seção 4.4** – Implementação e teste do GD com PyTorch
6. **Seção 4.5** – Comparação dos três métodos

---

## Entrega

Arquivo: `joao.lima_lab1.zip` contendo o notebook `.ipynb` e o relatório `.pdf`.
