# 🛡 Detecção de Ataques DDoS em Tráfego de Rede com ML

Projeto de TCC de **Camilly Pinto de Souza** – Curso Superior de Tecnologia em Redes de Computadores, **IFPB**.

O objetivo deste projeto é realizar uma **análise comparativa entre Random Forest e Isolation Forest** para detecção de ataques DDoS em tráfego de rede, utilizando dados reais do dataset CSE-CIC-IDS2018.

---

## Estrutura do Repositório

```text
.
├── cross_validation.ipynb     #treinamento e avaliação dos modelos
├── Dataset/
│   ├── concat.ipynb     #notebook de criação da sample e EDA
│   └── OG-EDA.ipynb     #notebook de E.D.A dos CSV originais
├── .gitattributes
├── .gitignore
├── README.md

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

# Modelos Avaliados:

### Random Forest (Supervisionado)

- n_estimators=100,
- max_depth=15,           
- min_samples_split=5,    
- min_samples_leaf=2,     
- class_weight='balanced', 
- random_state=42,
- n_jobs=-1 

### Isolation Forest (Não supervisionado)

- n_estimators=500,        
- max_samples=0.6,         
- contamination='auto',      
- bootstrap=True,         
- random_state=42,
- n_jobs=-1

---

# 📈 Resultados (Resumo)

### ✔ Random Forest – Desempenho Alto
- Excelente capacidade de identificar ataques  
- Alta generalização entre folds

```bash
ACCURACY     Treino: 0.9990 | Teste: 0.9989 (±0.0001)
PRECISION    Treino: 0.9881 | Teste: 0.9873 (±0.0017)
RECALL       Treino: 0.9999 | Teste: 0.9995 (±0.0002)
F1           Treino: 0.9940 | Teste: 0.9934 (±0.0008)
ROC_AUC      Treino: 0.9994 | Teste: 0.9992 (±0.0001)
PR_AUC       Treino: 0.9880 | Teste: 0.9869 (±0.0016)
```

### ✔ Isolation Forest – Desempenho abaixo do esperado
- Detecção de anomalias mais difícil   
- Resultados insatisfátorios, má detecção de ataques.

```bash
ACCURACY     Média = 0.9258 | Desvio padrão = 0.0018
PRECISION    Média = 0.6188 | Desvio padrão = 0.0214
RECALL       Média = 0.2648 | Desvio padrão = 0.0208
F1           Média = 0.3707 | Desvio padrão = 0.0240
ROC_AUC      Média = 0.6251 | Desvio padrão = 0.0104
PR_AUC       Média = 0.2250 | Desvio padrão = 0.0164
```

---

# Como Executar?

1. **Clonar o repositório:**
```bash
git clone https://github.com/CamillypSouza/DDoS_Detection.git
cd DDoS_Detection
```
2. **obter os arquivos do dataset:**
[https://www.unb.ca/cic/datasets/ids-2017.html]
Neste link, são disponibilizadas mais informações sobre o dataset completo, bem como o download do mesmo.
Apenas os arquivos 'Thuesday-20-02-2018_TrafficForML_CICFlowMeter.csv' e 'Wednesday-21-02-2018_TrafficForML_CICFlowMeter.csv' serão necessários.

3. **Gerar a sample final executando o notebook:**
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
