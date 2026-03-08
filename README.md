# Análise de Capacidade e Otimização de Estoque por Filial

## 📌 Sobre o Projeto

Este projeto consiste em um dashboard interativo desenvolvido no **Power BI** para analisar e monitorar a capacidade de preenchimento de estoque em uma rede de filiais de varejo. 

O objetivo central é comparar a infraestrutura física (capacidade de equipamentos, modelos e peças) com o volume de estoque atual, permitindo que gestores identifiquem, de forma rápida, gargalos de espaço, superalocação ou subutilização de recursos em cada loja.

### 💡 Por que este projeto é importante?

No ambiente de varejo de alto volume, a gestão eficiente do espaço de loja é crítica. Este dashboard traz transparência para as seguintes questões de negócio:

* **Evitar Ruptura de Estoque:** Ao monitorar a relação de famílias completas/incompletas, garante-se que os produtos certos estejam disponíveis para venda, otimizando o sortimento.
* **Otimização de Espaço:** Ajuda a identificar filiais que operam acima de sua capacidade teórica, permitindo a redistribuição estratégica de mercadorias.
* **Apoio à Decisão Estratégica:** Fornece dados concretos para planejar expansões, readequações de layout de loja ou novas estratégias de compras baseadas na capacidade real de cada setor.
* **Eficiência Operacional:** Permite que as equipes de loja tenham clareza sobre quais setores precisam de atenção imediata em relação ao reabastecimento ou organização.

---

## 🛡️ Disclaimer e Privacidade (Dados Anonimizados)

Para fins de exibição pública e proteção de dados sensíveis:
* **Anonimização:** Todos os dados de filiais, cidades e valores foram alterados para dados sintéticos/fictícios.
* **Nomenclatura:** Os nomes das tabelas (ex: `fClusterLojaSetor`), bem como variáveis de negócio e medidas, foram renomeados ou abstraídos em relação ao modelo de produção original para garantir a segurança da propriedade intelectual.

---

## 🏗️ Estrutura de Dados e Relacionamentos

A modelagem de dados segue as melhores práticas de Business Intelligence, utilizando um esquema que conecta tabelas fato e dimensão de forma otimizada.

<img width="1296" height="830" alt="modelo-dados" src="https://github.com/user-attachments/assets/969d605f-b17d-48d6-aeef-75eba2d1c003" />

*Figura 1: Esquema de Dados e Relacionamentos.*

### Entidades do Modelo:

* **fFamiliasFilialSetor (Fato):** Centraliza métricas sobre a completude do mix de produtos (famílias) por setor.
* **fClusterLojaSetor (Fato Central):** Tabela principal que contém os indicadores de capacidade física, volumetria de peças e estoque por filial.
* **dFiliais (Dimensão):** Atributos geográficos e cadastrais das unidades de negócio.
* **_Medidas (Tabela de Medidas):** Centraliza todas as regras de negócio escritas em DAX.

---

## 🛠️ Detalhes das Visões (Relatório Power BI)

O relatório é dividido em duas visões principais para permitir uma análise macro (Filial) e micro (Setor).

### 1. Visão Geral: Capacidade de Estoque por Loja

Esta visão apresenta uma tabela analítica comparativa que serve como o primeiro nível de diagnóstico para a rede.

**Destaques:**
* **Análise de Infraestrutura:** Comparativo entre capacidade teórica (Equipamentos/Modelos) vs. Estoque Real.
* **Conceito de Famílias:**
    * **Família Completa:** Sortimento 100% presente na unidade.
    * **Família Incompleta:** Sortimento com faltas ou rupturas parciais.
* **Benchmarking:** Linha de totais que permite identificar filiais fora da curva de ocupação média.

<img width="1444" height="810" alt="modulacao-loja" src="https://github.com/user-attachments/assets/f3a95def-e346-402a-aa5a-c2bbd3bcb2f3" />

*Figura 2: Tabela Analítica por Unidade de Negócio.*

---

### 2. Visão Detalhada: Capacidade de Estoque por Setor

Focada no desempenho granular, esta visão permite entender como cada categoria de produto ocupa o espaço disponível na loja.

**Destaques:**
* **Indicadores-Chave (KPIs):** Totalizadores de peças, volume absoluto de estoque e o percentual de ocupação em relação à meta.
* **Status de Meta:** Gráfico de barras com formatação condicional.
    * **Azul:** Setor operando dentro dos limites esperados.
    * **Vermelho:** Setores com desvios superiores a 10% da meta de capacidade (superlotados ou subutilizados).

<img width="1442" height="810" alt="modulacao-setor" src="https://github.com/user-attachments/assets/2ec63fe5-854b-4b62-b429-44b3d83b4a3a" />

*Figura 3: Visão Setorial com Indicadores de Performance
