# Dashboard de Análise de Capacidade e Otimização de Estoque por Filial

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

## 🏗️ Estrutura de Dados e Relacionamentos

A modelagem de dados foi desenhada para suportar análises performáticas, utilizando um esquema que conecta as tabelas de fato com tabelas de dimensão e uma tabela de medidas centralizada.

<img width="1296" height="830" alt="modelo-dados" src="https://github.com/user-attachments/assets/969d605f-b17d-48d6-aeef-75eba2d1c003" />

*Figura 1: Esquema de Dados Profissional.*

### Entidades do Modelo (detalhadas na figura):

* **fFamiliasFilialSetor (Fato):** Centraliza métricas sobre completude de sortimento por loja e setor (Famílias Completas, Incompletas, Inválidas, Total).
* **fClusterLojaSetor (Fato Central):** A tabela 'âncora' que conecta as métricas operacionais e financeiras por loja/setor (Estoque Custo, Qtd, Peças, etc.) com as outras entidades.
* **dFiliais (Dimensão):** Cadastro das lojas (Filial, Cidade, Nome, Região). Relacionada via campo `Filial`.
* **_Medidas (Tabela de Medidas):** Centraliza as medidas DAX (`% Estoque Disponível`, `_Estoque Qtd`, etc.).

---

## 🛠️ Detalhes das Visões (Relatório Power BI)

O relatório é dividido em duas visões complementares: uma focada no desempenho geral das filiais e outra focada no desempenho detalhado por setor.

### 1. Visão Geral: Capacidade de Estoque por Loja

Esta visão apresenta uma tabela analítica comparativa para todas as filiais.

**Destaques:**
* **Análise de Infraestrutura:** Colunas para `Equipamentos`, `Modelos` e `Peças` para entender a capacidade teórica.
* **Estoque Atual:** Coluna `Estoque` para comparação direta com a capacidade.
* **Conceito de Famílias:**
    * **Família Completa:** Contagem de tipos de produtos que têm sortimento completo na loja.
    * **Família Incompleta:** Tipos de produtos com sortimento parcial.
    * **Família Total:** Contagem total de tipos de produtos distintos.
* **Totais Consolidados:** Uma linha de total na base para benchmarking da rede.

<img width="1444" height="810" alt="modulacao-loja" src="https://github.com/user-attachments/assets/f3a95def-e346-402a-aa5a-c2bbd3bcb2f3" />

*Figura 2: Tabela Analítica por Loja.*

---

### 2. Visão Detalhada: Capacidade de Estoque por Setor

Esta visão foca no desempenho granulado por categoria/setor, permitindo drill-down para áreas específicas.

**Destaques:**
* **Indicadores-Chave (KPI Cards):** Cards que mostram os totais agregados para `Qtd Peças`, `Estoque Qtd` e `% Estoque Disponível`.
* **Gráfico de Capacidade Setor:** Um gráfico de barras que compara o desempenho real (barras azuis/vermelhas) contra a meta (barras cinzas).
    * **Legenda Dinâmica:** As cores indicam se o setor está operando `Abaixo de 10% da Meta` ou `Acima de 10% da Meta`.

<img width="1442" height="810" alt="modulacao-setor" src="https://github.com/user-attachments/assets/2ec63fe5-854b-4b62-b429-44b3d83b4a3a" />

*Figura 3: Dashboard por Setor com Gráfico Comparativo.*

---

## 🚀 Como Executar o Projeto

1.  **Clone este repositório:**
    ```bash
    git clone [https://github.com/](https://github.com/)[SEU_USUARIO]/[NOME_DO_REPOSITORIO].git
    ```
2.  **Abra o arquivo Power BI:** Você precisará do **Power BI Desktop** instalado. Abra o arquivo `.pbix` localizado na pasta raiz.
3.  **Ajuste das Fontes de Dados:** Se necessário, vá em `Transformar Dados` para re-apontar para as fontes originais se os caminhos estiverem quebrados.
4.  **Publique:** Para visualização web, publique o relatório no seu workspace do Power BI Service.
