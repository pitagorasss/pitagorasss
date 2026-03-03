# 📊 Pipeline de Dados • ETL • Vendas • Gestão Comercial

![Python](https://img.shields.io/badge/Python-3.14-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.3.3-green)
![SQLite](https://img.shields.io/badge/SQLite-3-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)

Pipeline ETL desenvolvido em Python para integrar e padronizar dados de vendas e gerentes, transformando informações brutas em bases consistentes para análise.

---

## 🎯 Visão Geral

- **Extração**: leitura de arquivos CSV (vendas) e Excel (gerentes)
- **Transformação**: limpeza, padronização de datas, tratamento de nulos e remoção de duplicatas
- **Carga**: armazenamento em SQLite com relacionamento entre tabelas

---

## ❗ Problema

Dados de vendas e gerentes em formatos diferentes (CSV e Excel) apresentam:
- Valores nulos
- Datas com horários desnecessários
- Registros duplicados
- Falta de integridade relacional

---

## ✅ Solução

Pipeline automatizado que:
- Extrai dados de múltiplas fontes
- Padroniza formatos (datas sem hora)
- Trata nulos e remove duplicatas
- Carrega em banco relacional (SQLite)

---

## 📈 Resultado

Base única, limpa e consistente, pronta para análises confiáveis de desempenho de vendas por gerente, região e produto.

---

## 🛠️ Tecnologias

- Python 3.14
- Pandas
- SQLite3
- OpenPyXL

---

## 📁 Estrutura do Projeto
