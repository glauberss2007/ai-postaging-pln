# ai-postaging-pln

Este projeto implementa um sistema de **POS Tagging (Classificação Gramatical de Palavras)** utilizando o modelo BERT fine-tuned. O sistema é capaz de classificar palavras em textos em inglês em suas respectivas categorias gramaticais seguindo o padrão Universal Dependencies.

## Objetivos

- Implementar e avaliar um modelo de POS Tagging usando arquitetura BERT
- Analisar o desempenho por classe gramatical
- Identificar padrões de acurácia e desafios na classificação gramatical
- Fornecer insights sobre a capacidade do modelo em capturar nuances linguísticas

## Tecnologias Utilizadas

- **Python 3.8+**
- **Transformers** (Hugging Face)
- **PyTorch**
- **Datasets** (Hugging Face)
- **Scikit-learn**
- **Matplotlib & Seaborn**
- **Pandas & NumPy**

## Dataset

### Universal Dependencies - English EWT
- **Fonte**: Textos diversos da web (blogs, reviews, emails)
- **Tags**: 17 categorias gramaticais universais (UPOS)
- **Tamanho**: ≈ 16,000 sentenças anotadas
- **Split**: Treino/Validação/Teste

### Tags Gramaticais Utilizadas
```
ADJ, ADP, ADV, AUX, CCONJ, DET, INTJ, NOUN, NUM, 
PART, PRON, PROPN, PUNCT, SCONJ, SYM, VERB, X
```

## Implementação

### 1. Carregamento e Exploração do Dataset
- Análise da distribuição das classes gramaticais
- Verificação da qualidade e consistência dos dados
- Identificação de 17 categorias gramaticais padronizadas

### 2. Pré-processamento dos Dados
- Tokenização com BERT base uncased
- Alinhamento estratégico entre tokens e labels
- Tratamento de subpalavras e tokens especiais
- Divisão em conjuntos de treino/validação/teste

### 3. Treinamento do Modelo
- Fine-tuning do BERT para classificação de tokens
- Configuração: learning rate 2e-5, batch size 4, 2 épocas
- Métricas: Acurácia, Precision, Recall, F1-Score
- Framework: Hugging Face Trainer

### 4. Análise dos Resultados
- Avaliação detalhada por classe gramatical
- Visualizações de desempenho e distribuição
- Análise de correlação frequência-desempenho
- Identificação de padrões de erro

##  Resultados Obtidos

### Métricas Gerais
- **Acurácia Geral**: 64.71%
- **F1-Score Médio**: 53.79%
- **Correlação Frequência-Desempenho**: 0.239

### Melhores Classes (F1-Score)
1. **PUNCT** (Pontuação): 1.000
2. **ADP** (Preposições): 1.000
3. **DET** (Determinantes): 0.750
4. **ADJ** (Adjetivos): 0.615

### Classes com Desafios
- **VERB** (Verbos): 0.000
- **AUX** (Verbos Auxiliares): 0.000

## Insights e Observações

### Pontos Fortes
- Excelente desempenho em elementos estruturais (pontuação, preposições)
- Boa capacidade de identificar determinantes e adjetivos
- Modelo captura padrões gramaticais consistentes

### Desafios Identificados
- Dificuldade em distinguir verbos de outras categorias
- Baixa performance em classes com ambiguidade contextual
- Necessidade de mais dados para classes menos frequentes

### Análise Qualitativa
- Erros sistemáticos na classificação verbal
- Confusão entre adjetivos e substantivos em certos contextos
- Correlação fraca entre frequência e desempenho sugere complexidade linguística

##  Estrutura do Projeto

```
pos-tagging-bert/
├── pos_tagging_analysis.ipynb    # Notebook principal
├── pos_tagger/                   # Modelo treinado
├── pos_tagging_final_results.json # Resultados da análise
├── requirements.txt              # Dependências
└── README.md                     # Este arquivo
```

## Como Executar

1. **Instalar dependências:**
```bash
pip install accelerate>=0.26.0 transformers[torch] datasets scikit-learn matplotlib seaborn pandas numpy
```

2. **Executar o notebook:**
```bash
jupyter notebook pos_tagging_analysis.ipynb
```

## Visualizações Geradas

- **Gráfico de F1-Score por Classe**: Distribuição de desempenho
- **Frequência vs Desempenho**: Relação entre ocorrência e acurácia
- **Distribuição de Tags**: Proporção das classes gramaticais
- **Exemplos de Predições**: Análise qualitativa dos resultados

## Próximos Passos

- Expandir treinamento com mais épocas
- Experimentar com diferentes arquiteturas (RoBERTa, DeBERTa)
- Implementar técnicas para classes desbalanceadas
- Adicionar análise de erros mais detalhada
- Extender para outras línguas