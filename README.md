# Detecção de Ataques DDoS em Tráfego de Rede

## Análise Comparativa entre Random Forest e Isolation Forest

**Trabalho de Conclusão de Curso - IFPB Campus João Pessoa**

---

## 📌 Sobre o Projeto

Este repositório contém a implementação de um estudo comparativo entre algoritmos de aprendizado de máquina **supervisionado** (Random Forest) e **não supervisionado** (Isolation Forest) para detecção de ataques DDoS em tráfego de rede.

Os ataques distribuídos de negação de serviço (DDoS) representam uma das principais ameaças à segurança de redes de computadores. Este projeto investiga a eficácia de duas abordagens distintas de ML na detecção automatizada desses ataques.

### 🤖 Algoritmos Utilizados

| Algoritmo | Tipo | Características |
|-----------|------|-----------------|
| **Random Forest** | Supervisionado | Requer dados rotulados, alta precisão |
| **Isolation Forest** | Não Supervisionado | Detecção de anomalias sem rótulos prévios |

---

## 🎯 Objetivos

### Objetivo Geral

Investigar e comparar a eficácia dos algoritmos **Random Forest** e **Isolation Forest** na detecção de ataques DDoS, discutindo vantagens, limitações e aplicações práticas de cada abordagem.

### Objetivos Específicos

- Realizar pré-processamento completo dos dados do CSE-CIC-IDS2018
- Implementar e avaliar ambos os modelos
- Comparar desempenho através de múltiplas métricas
- Identificar features mais relevantes para detecção
- Avaliar viabilidade prática e robustez dos modelos

---

## 📂 Estrutura do Repositório

```
DDos_Detection_ML/
├── Dataset/
│   ├── concat.ipynb         # pré processamento, concatenação, geração da sample e análise exploratória 
│   ├── df_sample.csv
│   ├── Thuesday-20-02-2018_TrafficForML_CICFlowMeter.csv                       
│   └── Wednesday-21-02-2018_TrafficForML_CICFlowMeter.csv        
│      
├── cross_validation.ipynb   #Validação e comparação dos modelos
│
└── README.md
```

## 📚 Notebooks

### 1. `concat.ipynb`

**Objetivo:** O notebook tem o propósito de gerar uma amostra limpa a partir da concatenação de dois CSVs e realizar uma análise dessa amostra. Este notebook contém duas etapas:

###**ETAPA 1: Pré-processamento completo + geração da amostra**

**inclui:**
- Leitura otimizada de 2 grandes CSVs em chunks
- Seleção das colunas relevantes
- Limpeza e padronização dos dados
- Correção dos rótulos do dataset
- Remoção de features altamente correlacionadas
- Criação de uma amostra balanceada com ~600 mil fluxos
- Exportação do dataset final `df_sample.csv`

*Após remoção de duplicatas, o dataset final ficou em:*
- 535.925 benignos
- 48.302 ataques
- 584.227 linhas no total

###**ETAPA 2: Análise Exploratória (EDA)**

**inclui:**
- Distribuição das classes
- Estatísticas descritivas
- Correlações
- Outliers
- Portas e protocolos mais utilizados
- Padrões forward/backward
- Análise dos TCP Flags

---

### 3. `cross_validation.ipynb`

**Objetivo:** Realiza a avaliação completa dos modelos (RF e IF) utilizando o `df_sample.csv`. Executa validação cruzada, calcula múltiplas métricas e gera matrizes de confusão para comparar o desempenho dos modelos.

####**Metodologia de Validação:**

- **Técnica:** 5-Fold Stratified Cross-Validation
- **Métricas:** Accuracy, Precision, Recall, F1-Score, ROC AUC, PR AUC

---

## 📈 Resultados

**ainda em desenvolvimento**

---

## 💡 Principais Descobertas

### em desenvolvimento 

---
## 📊 Dataset Utilizado

### CSE-CIC-IDS2018

O dataset contém fluxos de tráfego de rede capturados usando o **CICFlowMeter** em ambiente controlado, incluindo múltiplos tipos de ataques.

**Download:** [Canadian Institute for Cybersecurity](https://www.unb.ca/cic/datasets/ids-2018.html)

---

## 🚀 Como Executar

### Pré-requisitos

```bash
# Python 3.12 ou superior
python --version

# Instalar dependências
pip install pandas numpy scikit-learn jupyter
```

### Ordem de Execução

#### 1. Consolidar dados brutos

```bash
jupyter notebook reduced-dataset.ipynb
```

**Output:** `df_total.csv`

#### 2. Preparar dataset otimizado

```bash
jupyter notebook Ajustes.ipynb
```

**Outputs:** `df_sample.csv`, `ranking_importancias_rf.csv`, `df_ddos.csv`

#### 3. Executar validação cruzada

```bash
jupyter notebook cross_validation.ipynb
```

**Output:** Métricas comparativas dos modelos

---

## 🔧 Tecnologias Utilizadas

| Tecnologia | Versão | Uso |
|------------|--------|-----|
| **Python** | 3.12 | Linguagem principal |
| **Pandas** | 2.0+ | Manipulação de dados |
| **NumPy** | 1.24+ | Operações numéricas |
| **Scikit-Learn** | 1.3+ | Machine Learning |
| **Jupyter** | Latest | Ambiente de desenvolvimento |

---

## 👥 Autoria

**Aluna:** Camilly Pinto de Souza

**Orientador:** Diego Ernesto Rosa Pessoa

**Instituição:** IFPB - Campus João Pessoa

**Curso:** Tecnólogo em Redes de Computadores

---

## 📄 Licença

Este projeto está sendo desenvolvido para fins **acadêmicos** como Trabalho de Conclusão de Curso (TCC).

---

## 📚 Referências

1. **Dataset CSE-CIC-IDS2018**  
   Canadian Institute for Cybersecurity  
   https://www.unb.ca/cic/datasets/ids-2018.html

2. **Scikit-learn Documentation**  
   Machine Learning Library for Python  
   https://scikit-learn.org

3. **Pandas Documentation**  
   Data Analysis Library  
   https://pandas.pydata.org

---

**Desenvolvido para a comunidade de Segurança de Redes**

**Última atualização:** Outubro 2025
