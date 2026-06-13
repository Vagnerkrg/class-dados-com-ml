# 🤖 Otimização de Modelos de Classificação com Machine Learning

`🐍 Python` `📦 v1.0.0`

Este é um projeto prático de Machine Learning focado no desenvolvimento, otimização de hiperparâmetros e validação robusta de pipelines para problemas de classificação, garantindo um código livre de viés de seleção.

## 🚀 Funcionalidades

* **Validação Cruzada Aninhada:** Avaliação real e sem viés do modelo usando loops combinados de `inner_cv` e `outer_cv`.
* **Sintonia Avançada:** Comparação direta de performance entre algoritmos tradicionais e métodos modernos de busca.
* **Métrica Estratégica:** Pipelines calibrados com foco absoluto em maximizar o **Recall** para mitigar falsos negativos.
* **Pipelines de Produção:** Fluxos integrados que garantem o tratamento e escalonamento correto de dados antes de cada inferência.

## 🛠️ Tecnologias Utilizadas

* **Python 3.12+**
* **Scikit-Learn** (Construção de pipelines, Árvores de Decisão e Regressão Logística)
* **Scikit-Optimize (skopt)** (Espaços de busca inteligentes e Otimização Bayesiana)
* **Pandas & Numpy** (Manipulação, engenharia de recursos e análise estrutural de dados)

## 📁 Estrutura de Modelos Salvos

Os artefatos finais gerados e validados no projeto foram serializados utilizando a biblioteca `pickle` e estão armazenados no diretório `/modelos`. Eles permitem realizar inferências imediatas sem a necessidade de reexecutar o processo de otimização:

* **`modelo_onehotenc.pkl`:** Pipeline contendo o transformador e pré-processamento das variáveis categóricas (One-Hot Encoding).
* **`modelo_arvore.pkl`:** O modelo final baseado no algoritmo de Árvore de Decisão com os melhores hiperparâmetros encontrados pela Otimização Bayesiana.

## 🔧 Como Executar o Projeto Localmente

1. Clone o repositório para sua máquina:
```bash
git clone https://github.com.git
```

2. Entre no diretório do projeto:
```bash
cd class-dados-com-ml
```

3. Instale as dependências necessárias:
```bash
pip install -r requirements.txt
```

4. Execute o notebook ou script de validação de sanidade:
```bash
python validacao.py
```

## ⚠️ Desafios Técnicos e Erros de Deploy Superados

Para colocar este ecossistema de Machine Learning 100% estável e funcional, foi necessário diagnosticar e corrigir uma série de erros críticos de infraestrutura e ambiente:

* **Incompatibilidade Binária (`ValueError: numpy.dtype size changed`):** Correção de conflito de ambiente onde o Pandas exigia uma versão mais atualizada e estável do Numpy do que a instalada por padrão.
* **Falta de Dependência Principal (`ModuleNotFoundError: No module named 'skopt'`):** Correção da quebra do pipeline em produção gerada pela falta da declaração explícita da biblioteca `scikit-optimize` no arquivo de requerimentos do projeto.
* **Incompatibilidade de Versões do Python (Preview vs Stable):** Correção de quebra de deploy gerada pelo uso de uma versão de testes muito recente (Python 3.14). O ambiente foi estabilizado ao fixar o interpretador para o **Python 3.12 estável** na máquina virtual.
* **Tratamento de Exceções no Pipeline:** Prevenção de quebras forçadas de código adicionando monitoramentos defensivos `try/except` para impedir o travamento da aplicação caso os hiperparâmetros gerem matrizes singulares ou erros de convergência.
* **Arquivos fora da Raiz do Repositório Git:** Reorganização da arquitetura de pastas, movendo o arquivo `requirements.txt` diretamente para a raiz (`root`) do repositório, permitindo a instalação automática e correta dos pacotes no GitHub.
