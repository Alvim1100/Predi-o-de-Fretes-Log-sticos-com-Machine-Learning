# 🚚 Predição de Fretes Logísticos com Machine Learning

Este projeto consiste em um pipeline completo de Ciência de Dados ("End-to-End"), desde a extração de dados em banco SQL até a criação de um modelo preditivo de precificação de fretes usando Python.

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![SQL](https://img.shields.io/badge/Database-PostgreSQL-336791)
![Status](https://img.shields.io/badge/Status-Concluído-success)

## 🎯 Objetivo do Projeto
O objetivo principal foi analisar o histórico de vendas de um E-commerce (Dataset Olist) para responder à pergunta: **"Quais variáveis realmente determinam o custo do frete no Brasil?"** e, a partir disso, criar uma IA capaz de prever custos para novos envios.

## 🛠️ Tecnologias e Ferramentas
* **SQL (PostgreSQL / pgAdmin 4):** Extração, filtragem e unificação de tabelas relacionais (JOINs e Views).
* **Python (Pandas & NumPy):** Limpeza de dados, engenharia de atributos e cálculos matemáticos.
* **Geopy / Haversine:** Cálculo de distância geodésica (considerando a curvatura da Terra) entre vendedor e cliente.
* **Scikit-Learn:** Criação, treino e validação do modelo de Machine Learning (Regressão Linear).

## 🧠 Principais Descobertas (Insights)
Durante a Análise Exploratória de Dados (EDA), refutei a hipótese comum de que a distância é o maior ofensor do preço.

| Variável | Correlação com Preço (Pearson) | Interpretação |
| :--- | :---: | :--- |
| **Volume (cm³)** | **0.92** | **Altíssima.** O espaço ocupado no caminhão é o fator determinante. |
| Peso (g) | 0.41 | Moderada. Menos relevante que o volume. |
| Distância (km) | 0.44 | Moderada. Impacta, mas menos do que o esperado. |

**Conclusão de Negócio:** A transportadora analisada opera com restrição de volume (cubagem), cobrando caro para transportar "ar" (caixas grandes e leves).

## 🤖 O Modelo de Machine Learning
Desenvolvi um modelo de **Regressão Linear Múltipla** que aprendeu a seguinte fórmula de precificação:

$$Preço = 7.50 + (0.0107 \times Distância) + (0.0004 \times Volume)$$

* **Taxa Fixa (Base):** R$ 7.50
* **Custo por KM:** R$ 0.01
* **Custo por cm³:** R$ 0.0004

### Exemplo de Previsão Real
Para o envio de uma **Geladeira** (80.000 cm³) a uma distância de **50 km**:
* **Preço Previsto:** R$ 40,02
* *Validado como coerente com valores de mercado para frete urbano de grandes volumes.*

## 🚀 Como Executar
1.  Clone este repositório.
2.  Instale as dependências: `pip install pandas numpy scikit-learn`
3.  Execute o Jupyter Notebook `PrevisaoFretes.ipynb`.
4.  Ao final do notebook, utilize o **Simulador Interativo** para testar seus próprios cenários de distância e volume.

---
*Desenvolvido por [Eric Weber Alvim] como projeto de portfólio em Data Analytics.*
