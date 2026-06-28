# AC_Arboviroses_Pe
Modelo de Autômatos Celulares para simulação acadêmica (UFRPE) de disseminação de arboviroses (dengue, chikungunya, zika) em Pernambuco,  integrado com dados reais do SINAN.

## 📝 Descrição Completa para o Repositório **AC_Arboviroses_Pe**

---
# AC_Arboviroses_Pe  
Autômatos Celulares para Simulação de Arboviroses em Pernambuco

---

## 📋 Sobre o Projeto  
Este repositório combina **modelagem matemática (Autômatos Celulares)** com **dados epidemiológicos reais** para estudar a disseminação de arboviroses (dengue, chikungunya, zika) em Pernambuco. O projeto utiliza um pipeline completo de validação de dados do SINAN (Sistema de Informação de Agravos de Notificação) e implementa um modelo SIR (Suscetível-Infectado-Recuperado) adaptado para dinâmicas espaciais.

---

## ✨ Principais Funcionalidades  
- 🦟 **Modelo SIR-AC**: Autômato celular com vizinhança de Moore para simulação espacial  
- 📊 **Integração com Dados Reais**: Conexão com banco DuckDB contendo **33,6 milhões de registros do SINAN**  
- 🔬 **Calibração Histórica**: Ajuste de parâmetros usando picos epidêmicos reais (ex: 2015-2016, 2024)  
- 🎭 **Simulação de Cenários**: Testa intervenções como vacinação em massa e controle do vetor *Aedes aegypti*  
- 📈 **Visualizações**: Gráficos de evolução temporal, estados do grid e animações  
- 🧹 **Pipeline de Qualidade**: Validação, limpeza e padronização de dados já implementada  

---

## 🛠️ Stack Tecnológica  
| Ferramenta               | Propósito                                  |
|--------------------------|--------------------------------------------|
| Python 3.x               | Linguagem principal                        |
| DuckDB                   | Processamento de dados grandes             |
| NumPy                    | Cálculos numéricos do autômato             |
| Matplotlib               | Visualizações gráficas                     |
| Pandas/PyArrow           | Manipulação de dados Parquet/CSV           |

---

## 📂 Estrutura do Repositório  
```
AC_Arboviroses_Pe/
├── 01_pipeline_validacao.py          # Leitura e validação dos dados SINAN
├── 02_inventario_variaveis.py        # Inventário de variáveis do dataset
├── 03_padronizacao_variaveis.py      # Padronização de tipos de dados
├── automato_celular_arboviroses.py   # Implementação do Autômato Celular SIR
├── GUIA_AUTOMATOS_CELULARES.md       # Guia teórico de AC e epidemiologia
├── TUTORIAL_INTEGRACAO.md            # Tutorial para integrar dados de PE
├── config.py                         # Configurações globais do projeto
├── utils.py                          # Funções utilitárias reutilizáveis
└── README.md                         # Este arquivo!
```

---

## 🚀 Como Usar  
1. **Instale as dependências**:  
   ```bash
   pip install duckdb pandas numpy matplotlib pyarrow openpyxl
   ```

2. **Prepare os dados**:  
   Coloque os arquivos Parquet do SINAN na pasta raiz (ex: `dengue_00_06.parquet`).

3. **Execute o pipeline de dados**:  
   ```bash
   python 01_pipeline_validacao.py
   python 02_inventario_variaveis.py
   python 03_padronizacao_variaveis.py
   ```

4. **Simule o Autômato Celular**:  
   ```bash
   python automato_celular_arboviroses.py
   ```

---

## 📊 Dados Utilizados  
| Característica          | Detalhes                                  |
|--------------------------|--------------------------------------------|
| Fonte                    | SINAN/MS (Ministério da Saúde do Brasil)  |
| Período                  | 2000–2026                                  |
| Total de Registros       | 33,6 milhões (Brasil) + 227.566 (PE)      |
| Arboviroses              | Dengue, Chikungunya, Zika, Febre de Mayaro|

---

## 🎯 Casos de Uso  
- 📚 Pesquisa acadêmica em epidemiologia  
- 🏥 Planejamento de intervenções de saúde pública  
- 🎓 Educação em modelagem matemática de doenças  
- 📊 Análise de cenários epidêmicos históricos/futuros  

---

## 📄 Licença  
Este projeto está sob a **Licença MIT** — veja o arquivo LICENSE para detalhes.

---

## 🙏 Agradecimentos  
- Ministério da Saúde do Brasil pelo SINAN  
- IBGE por dados geográficos e demográficos  
- Comunidade Python por bibliotecas incríveis  

---
