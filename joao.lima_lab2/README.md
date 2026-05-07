# Laboratório 2 – Aprendizado Profundo (Imitation Learning)

**Instituto Tecnológico de Aeronáutica – ITA**
**Disciplina:** Aprendizado Profundo – CM-204
**Professor:** Marcos Ricardo Omena de Albuquerque Maximo

---

## Descrição

Implementação de uma rede neural *feedforward* com **PyTorch** para realizar **aprendizado por imitação** (*imitation learning*) do movimento de caminhar de um robô humanoide. A rede aprende a copiar as trajetórias angulares das juntas do robô a partir de demonstrações de um algoritmo de controle clássico.

---

## Problema

O dataset contém as **posições angulares das 20 juntas** do robô durante um ciclo de caminhada, capturadas enquanto o robô caminhava com um controlador baseado em teoria de Controle. A rede neural aprende a mapear o tempo → posição de cada junta, copiando o comportamento do controlador original.

### Juntas modeladas (exemplo – perna direita)

`rightAnklePitch`, `rightAnkleRoll`, `rightHipPitch`, `rightHipRoll`, `rightHipYaw`, `rightKneePitch`

---

## Tarefas

| Seção | Tarefa |
|-------|--------|
| 4.1   | Estudo de implementação de rede neural com PyTorch |
| 4.2   | Análise do efeito de regularização L2 (classificação binária) |
| 4.3   | Implementação da rede para *imitation learning* |

### Seção 4.2 – Regularização L2

Treina uma rede para duas tarefas de classificação:
- `sum_gt_zero`: $x_1 + x_2 \geq 0$
- `xor`: $x_1 \oplus x_2$

Testa com `lambda_l2 = 0.000` e `lambda_l2 = 0.002` para visualizar o efeito nos limites de decisão.

---

## Configuração do Treinamento (Imitation Learning)

| Parâmetro      | Valor                          |
|----------------|--------------------------------|
| Arquitetura    | Linear → LeakyReLU → ... → Linear |
| Camadas        | 1 → 75 → 50 → 20 neurônios    |
| Ativação       | LeakyReLU (α = 0.01)           |
| Épocas         | 30.000                         |
| Batch size     | Tamanho total do dataset       |
| Otimizador     | Adam (lr = 1e-4)               |
| Função de perda| MSELoss                        |

---

## Estrutura do Projeto

```
joao.lima_lab2/
├── joao_lima_lab2.ipynb     # Notebook principal
├── joao_lima_lab2.pdf       # Relatório
└── lab2_results/            # Gráficos de trajetórias das juntas
```

---

## Como Executar

### Pré-requisitos

```bash
pip install torch numpy matplotlib
```

### Execução

Abra e execute o notebook `joao_lima_lab2.ipynb` em ordem:

1. **Célula download** – Baixa os dados e `utils.py`
2. **Seção 4.1** – Estudo do código base de rede neural
3. **Seção 4.2** – Experimentos com regularização L2
4. **Seção 4.3** – Treinamento da rede de imitation learning e visualização das trajetórias

---

## Entrega

Arquivo: `joao.lima_lab2.zip` contendo o notebook `.ipynb` e o relatório `.pdf`.
