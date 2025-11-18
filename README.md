# 🛡 Detecção de Ataques DDoS em Tráfego de Rede com ML

Projeto de TCC de **Camilly Pinto de Souza** – Curso Superior de Tecnologia em Redes de Computadores, **IFPB**.

O objetivo deste projeto é realizar uma **análise comparativa entre Random Forest e Isolation Forest** para detecção de ataques DDoS em tráfego de rede, utilizando dados reais do dataset CSE-CIC-IDS2018.

---

## Estrutura do Repositório

```text
.
├── cross_validation.ipynb      # Notebook principal para treinamento e avaliação dos modelos
├── Dataset/
│   ├── Thuesday.zip            # Dados de tráfego coletados na terça-feira
│   ├── wednesday.zip           # Dados de tráfego coletados na quarta-feira
│   ├── concat.ipynb            # Notebook para limpeza/concatenação dos datasets/ análise exploratória
│   └── df_sample.zip           # Amostra final do dataset balanceada

```
---
## Pré-requisitos

- Python >= 3.8  
- Bibliotecas:
  - pandas
  - numpy
  - scikit-learn
  - matplotlib
  - seaborn

Instale as dependências com:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```
---
# 📊 Dataset

O dataset utilizado é derivado do **CIC-IDS 2018**, contendo tráfego de rede benigno e malicioso, já processado pelo **CICFlowMeter**.

Após limpeza e seleção de colunas, o dataset final possui:

| Propriedade     | Valor                        |
|-----------------|------------------------------|
| Linhas          | 584.227                      |
| Features        | 19                           |
| Label           | 0 = Normal, 1 = DDoS         |
| Distribuição    | 91.7% normal • 8.3% ataque  |

---

# Etapas Principais de Pré-Processamento

- ✔ Concatenação dos arquivos **Thuesday** e **Wednesday**  
- ✔ Remoção de colunas inconsistentes  
- ✔ Normalização dos nomes das labels  
- ✔ Transformação da coluna **Label → binária (0/1)**  
- ✔ Padronização com **StandardScaler** (apenas para modelos não supervisionados)  
- ✔ Criação da amostra final **df_sample.csv**

---

# 🧪 Modelos Avaliados

### Random Forest (Supervisionado)

- Treinado utilizando **StratifiedKFold (5 folds)**  
- Balanceamento via `class_weight="balanced"`  

### Isolation Forest (Não supervisionado)

- Treinado apenas com tráfego benigno  
- `contamination='auto'`  
- Padronização via **StandardScaler**  
- 500 árvores e amostragem **bootstrap**

---

# 📈 Resultados (Resumo)

### ✔ Random Forest – Desempenho Alto
- Excelente capacidade de identificar ataques  
- Alta generalização entre folds  

### ✔ Isolation Forest – Desempenho Mediano
- Detecção de anomalias mais difícil   
- Resultados aceitáveis, mas inferiores ao modelo supervisionado

---

# Como Executar?

1. **Clonar o repositório:**
```bash
git clone https://github.com/CamillypSouza/DDoS_Detection.git
cd DDoS_Detection
```
2. **Descompactar os arquivos do dataset:**
/Dataset/Thuesday.zip
/Dataset/Wednesday.zip

3. **Gerar o dataset final executando o notebook:**
Dataset/concat.ipynb

4. **Executar a validação cruzada:**
cross_validation.ipynb

---

# 📚 Referências

- **CIC-IDS 2018 Dataset** – Canadian Institute for Cybersecurity  
- **Scikit-learn Documentation**  
- Pesquisas recentes sobre detecção de anomalias em tráfego de rede  

---

# 📝 Licença

Este projeto é **para fins educacionais e acadêmicos**.  
Sinta-se livre para utilizar como base em estudos ou trabalhos científicos.
