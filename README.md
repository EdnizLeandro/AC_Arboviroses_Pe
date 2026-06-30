# Dashboard de Arboviroses - Pernambuco (2000-2026)

<p align="center">
  <img alt="Python" src="https://img.shields.io/badge/Python-3.13+-blue?style=flat-square&logo=python">
  <img alt="Streamlit" src="https://img.shields.io/badge/Streamlit-Framework-red?style=flat-square&logo=streamlit">
  <img alt="Pandas" src="https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=flat-square&logo=pandas">
  <img alt="Plotly" src="https://img.shields.io/badge/Plotly-Visualizations-3F4F75?style=flat-square&logo=plotly">
  <img alt="License" src="https://img.shields.io/badge/License-MIT-green?style=flat-square">
</p>

## Descrição Geral

Este projeto implementa um **dashboard interativo** para análise de dados de **arboviroses** (dengue, zika e chikungunya) no estado de Pernambuco, Brasil, no período de 2000 a 2026. A ferramenta integra dados do **Sistema de Informação de Agravos de Notificação (SINAN)** com informações socioeconômicas dos municípios de Pernambuco do **Instituto Brasileiro de Geografia e Estatística (IBGE)**, além de um **modelo de autômato celular** para simular a propagação das arboviroses usando o modelo SIR.

## Funcionalidades Principais

O dashboard é composto por 5 páginas principais:

1. **Visão Geral dos Dados**
   - Indicadores principais (total de casos, idade média, taxa de hospitalização, taxa de óbito)
   - Gráficos de tendências temporais
   - Distribuição por sexo e classificação final
   - Top municípios por casos
   - Principais sintomas
   - Filtros interativos por ano, classificação e sexo

2. **Municípios de PE**
   - Lista completa dos 186 municípios pernambucanos
   - Dados socioeconômicos detalhados (população, área, IDH, PIB per capita)
   - Casos de arboviroses por município
   - Gráficos de tendências por município selecionado

3. **Simulação com Autômato Celular Dinâmico**
   - Modelo SIR implementado com autômato celular
   - Parâmetros ajustáveis (taxa de transmissão, taxa de recuperação, tamanho da grade, etc.)
   - Controles de play/pausa/passo
   - Visualização do estado do grid em tempo real
   - Gráfico de evolução temporal dos compartimentos (Suscetível, Infectado, Recuperado)

4. **Dicionário de Dados - SINAN**
   - Documentação completa das variáveis do SINAN utilizadas
   - Descrições e categorias para cada campo

5. **Sobre o Projeto**
   - Visão geral do projeto
   - Fonte dos dados
   - Tecnologias utilizadas

## Estrutura do Repositório

```
.
├── app.py                          # Arquivo principal do Streamlit (OBRIGATÓRIO)
├── requirements.txt                # Lista de dependências Python (OBRIGATÓRIO)
├── README.md                       # Documentação do projeto (OBRIGATÓRIO)
│
├── arbovirose_final_pe.parquet     # Dataset de arboviroses (SINAN)
└── Municipios de Pe.xlsx           # Dados dos municípios (IBGE)
```

## Como Executar

### Pré-requisitos

- Python 3.13 ou superior
- pip (gerenciador de pacotes Python)

### Instalação

1. **Clone o repositório**
   ```bash
   git clone <URL_DO_REPOSITORIO>
   cd <PASTA_DO_REPOSITORIO>
   ```

2. **Instale as dependências**
   ```bash
   pip install -r requirements.txt
   ```

3. **Execute o dashboard**
   ```bash
   streamlit run app.py
   ```
   - O dashboard abrirá automaticamente no navegador padrão
   - Se não abrir, acesse: `http://localhost:8501`

## Requisitos do Sistema

- Sistema Operacional: Windows, macOS ou Linux
- Memória RAM: 4GB (8GB recomendado para performance)
- Armazenamento: 500MB de espaço livre (para o dataset Parquet)

## Fonte dos Dados

| Fonte | Período | Tipo |
|-------|---------|------|
| **SINAN** (Ministério da Saúde) | 2000-2026 | Casos de arboviroses |
| **IBGE** | 2010-2025 | Dados socioeconômicos dos municípios |

## Validação de Dados

Um pipeline completo de validação de dados foi implementado para garantir a qualidade das análises. Os principais problemas identificados e corrigidos:

1. **Campo `NU_IDADE_N`**: Valores codificados com offset de 4000. Solução: Uso de estimativas de idade média por ano baseadas em boletins epidemiológicos (≈ 31 anos).
2. **Campo `ID_MUNICIP`**: Inconsistência no formato dos códigos (6 vs. 7 dígitos). Solução: Normalização para 6 dígitos.
3. **Campo `CS_SEXO`**: Valores vazios. Solução: Filtro de registros inválidos.
4. **Campo `CLASSI_FIN`**: Altas taxas de valores nulos (22,23%). Solução: Tratamento como dados faltantes.

O relatório completo de validação de dados está disponível em `Artigo/RELATORIO_PRINCIPAL_VALIDACAO_DADOS.md`.

## Tecnologias Utilizadas

| Tecnologia | Versão | Uso |
|------------|--------|-----|
| **Python** | 3.13+ | Linguagem de programação |
| **Streamlit** | Última | Framework para dashboards |
| **Pandas** | Última | Análise e manipulação de dados |
| **Plotly** | Última | Visualizações gráficas interativas |
| **NumPy** | Última | Computação numérica |
| **Matplotlib** | Última | Visualizações 2D (autômato celular) |
| **PyArrow** | Última | Leitura de arquivos Parquet |
| **OpenPyXL** | Última | Leitura de arquivos Excel |

## Documentação Adicional

- **Artigo sobre o Projeto**: `Artigo/Artigo_Arboviroses_Pernambuco.md` - Documento completo com introdução, metodologia, resultados e discussão.
- **Relatório de Validação de Dados**: `Artigo/RELATORIO_PRINCIPAL_VALIDACAO_DADOS.md` - Detalhes do pipeline de validação e qualidade dos dados.
- **Dicionário de Dados**: Disponível no dashboard na página "Dicionário de Dados".

## Licença

Este projeto está licenciado sob a **Licença MIT**. Consulte o arquivo `LICENSE` para mais detalhes.

## Autor

**Edniz Leandro**

## Agradecimentos

- **Secretaria Estadual de Saúde de Pernambuco** - Fornecimento dos dados do SINAN.
- **Instituto Brasileiro de Geografia e Estatística (IBGE)** - Dados socioeconômicos dos municípios.
- **Equipe Streamlit** - Framework incrível para construção de dashboards.

---
