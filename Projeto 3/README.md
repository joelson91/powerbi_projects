## Objetivo do ETL

Este processo de ETL tem como finalidade extrair informações do banco de dados **Azure Company** para responder as seguintes perguntas de negócio:

- Quantos colaboradores existem por departamento?
- Quais departamentos têm o maior número de colaboradores?
- Quem é o gerente de cada colaborador?
- Em qual cidade está localizado cada departamento?
- Há quantas horas trabalhadas por cada colaborador?
- Há quantas horas trabalhadas por departamento?

As métricas e indicadores chave de desempenho (KPIs) que serão gerados a partir dos dados são:

- Número de colaboradores por departamento.
- Número de colaboradores por gerente.
- Localização de cada departamento.
## Fonte de Dados

Os dados são extraídos de um banco de dados **MySQL** hospedado no servidor **Azure**, utilizando o banco de dados **Azure Company**. As credenciais de acesso (usuário e senha) são fornecidas durante a configuração da conexão no Power BI.
## Transformação de Dados com Power Query

1. **Renomeação das tabelas:** As tabelas foram renomeadas para nomes mais intuitivos e significativos, facilitando a compreensão do modelo de dados.
2. **Remoção de colunas desnecessárias em todas as tabelas:** Colunas que não serão utilizadas nas análises foram removidas para otimizar o desempenho e reduzir o tamanho do modelo.
3. **Renomeação das colunas em todas as tabelas:** As colunas foram renomeadas para nomes mais claros e significativos, seguindo as convenções de nomenclatura do projeto.
4. **Ajuste do tipo de coluna nas seguintes tabelas:**
    - **Colaborador:** A coluna "Salário" foi convertida para o tipo `decimal fixo` para facilitar o cálculo de valores monetários.
    - **Trabalha Em:** A coluna "Horas" foi convertida para o tipo `inteiro` para permitir análises sobre o tempo de trabalho.
5. **Divisão da coluna "Nome Completo" na tabela "Colaborador" em duas novas colunas: "Nome" e "Sobrenome":** Esta etapa é necessária para separar o nome e o sobrenome dos colaboradores, permitindo análises mais detalhadas por nome ou sobrenome.
6. **Divisão da coluna "Endereço" na tabela "Colaborador" em duas novas colunas: "Endereço", "Cidade" e "Estado":** Esta etapa facilita a exibição da localização em relatórios e visuais.
## Consultas

1. **Consulta Colaborador por Departamento:** Retorna todos os colaboradores de cada departamento, utilizando as tabelas "Colaborador" e "Departamento".
2. **Consulta Colaborador por Gerente:** Retorna o gerente de cada colaborador, utilizando a tabela "Colaborador".
3. **Consulta Departamento por Localização:** Retorna a cidade de cada departamento, utilizando as tabelas "Departamento" e "Localização".