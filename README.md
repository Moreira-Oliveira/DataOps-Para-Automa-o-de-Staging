# DataOps-Para-Automacao-de-Staging

📚DataOps Para Automação de Staging e Data Warehousing com Airbyte, dbt, SQL e Snowflake.

Um projeto de DataOps totalmente prático e abrangente, que integra diversas ferramentas e plataformas para implementar uma solução completa. O fluxo abrange desde a extração de dados brutos de um ambiente local até sua transferência para uma área de Staging na nuvem, seguida pela limpeza, transformação e automação da criação de um Data Warehouse na nuvem. O projeto utiliza um Modern Data Stack composto por Airbyte, dbt, SQL e a plataforma Snowflake.

![Image](https://github.com/user-attachments/assets/85958bc2-8123-4401-aa2e-52b18313aa6d)

📚 Estratégias de Backup e Recuperação para Data Warehouse na Nuvem

Garantir alta disponibilidade, integridade dos dados e tempos mínimos de inatividade é essencial para backups e recuperação em Data Warehouses na nuvem. As principais abordagens incluem:

1. Backup Incremental e Completo

* Incremental: Armazena apenas os dados alterados ou adicionados desde o último backup, otimizando custos e espaço de armazenamento.

* Completo: Realiza uma cópia integral de todo o Data Warehouse (DW) periodicamente, garantindo uma recuperação consistente.

2. Snapshots Automatizados

* Snapshots de Cloud Providers: Serviços como AWS Redshift, Google BigQuery e Snowflake permitem configurar snapshots automatizados em intervalos regulares.

* Restauração Fácil: Snapshots facilitam a recuperação rápida do ambiente para um ponto específico no tempo.

3. Estratégias de Retenção e Arquivamento

* Retenção Personalizada: Estabeleça períodos de retenção diferenciados para backups diários, semanais e mensais.

* Arquivamento de Dados Antigos: Mova dados pouco acessados para soluções de armazenamento de baixo custo, como AWS S3 Glacier ou Google Coldline.

4. Replicação Geográfica

* Multirregional: Replicar o DW em várias regiões geográficas ajuda a mitigar falhas localizadas.

* Alta Disponibilidade: Minimiza impactos causados por falhas de hardware ou interrupções em datacenters específicos.

5. Logs de Transação e Replays

* Logs de Mudança: Configure logs de transação ou logs de alteração (change data capture) para rastrear modificações nos dados.

* Replays de Logs: Utilize os logs para restaurar dados até o ponto exato da falha, em caso de interrupções.

6. Testes Regulares de Recuperação

* Simulação de Falhas: Realize testes periódicos para validar a eficácia dos processos de recuperação.

* Redução de Riscos: Assegure que os backups estão completos, utilizáveis e que os tempos de recuperação atendem aos requisitos do negócio.

7. Estratégias de Versionamento

* Versionamento de Dados: Mantenha diferentes versões de dados críticos para proteger contra exclusões ou alterações acidentais.

* Tabelas Temporais: Utilize recursos como "Time Travel" no Snowflake para acessar versões anteriores dos dados.

8. Backups Multi-Cloud

* Redundância Multi-Cloud: Replique backups entre diferentes provedores de nuvem para evitar dependência de um único fornecedor.

* Proteção Adicional: Oferece segurança contra falhas generalizadas de um provedor específico.

9. Automação com Ferramentas de Backup

* Ferramentas Nativas: Adote soluções dos provedores de nuvem, como AWS Backup ou Azure Backup.

* Integrações com Terceiros: Utilize ferramentas como Veeam, Rubrik ou Druva para automatizar e gerenciar backups em ambientes multicloud.

10. Planos de Recuperação de Desastres (DRP)

* Procedimentos Documentados: Desenvolva e documente planos detalhados de recuperação para diversos cenários de falhas.

* Definição de RTO e RPO: Estabeleça tempos máximos de recuperação (RTO) e perdas de dados aceitáveis (RPO) com base nos requisitos do negócio.

11. Proteção Contra Exclusões e Corrupções

* Backups Imutáveis: Configure backups que não possam ser alterados ou excluídos durante um período definido, garantindo proteção contra alterações indesejadas.

* Validação Automática de Backups: Implemente processos automatizados para verificar regularmente a integridade e a consistência dos backups.

12. Monitoramento e Alertas

* Monitoramento Contínuo: Estabeleça alertas para falhas nos processos de backup ou para alterações inesperadas nos dados.

* Respostas Proativas: Habilite intervenções rápidas para corrigir problemas antes que impactem operações críticas.

Essas estratégias devem ser personalizadas de acordo com as necessidades do negócio, o volume de dados e as regulamentações aplicáveis. Uma abordagem integrada que combine automação, redundância e testes regulares é essencial para assegurar a segurança e a disponibilidade dos dados.

📚 Programa utilizado

* Airbyte
* Docker
* PostgreSQL
* Snowflake
* DBT

Para este projeto, usaremos como fonte de dados um banco de dados do PostgreSQL. Para preparar a massa de dados, vamos restaurar um banco de dados que será baixado na pasta deste projeto. Após baixar o arquivo, é só conectar a fonte de dados no PostgreSQL.

* Resultado:

![Image](https://github.com/user-attachments/assets/42d500e6-5ac1-42b5-bf41-77721330931b)

📚 Schema do banco de dados

![Image](https://github.com/user-attachments/assets/8f3b8cbb-19a6-4781-8547-c62d66880174)

📚 Configurando a área de staging no Snowflake (configuração no arquivo txt)

A área de staging em um projeto de Data Warehouse tem como objetivo atuar como uma zona intermediária para o armazenamento temporário de dados brutos provenientes de diferentes fontes. Nessa etapa, os dados são carregados sem transformações significativas, permitindo a consolidação, validação e integração antes de serem processados, transformados e carregados para camadas subsequentes do Data Warehouse, como a camada de integração ou de apresentação. Isso garante maior flexibilidade e controle sobre a qualidade dos dados.

![Image](https://github.com/user-attachments/assets/022ca950-6828-46e3-907e-1fcbb2526f70)

📚 Configurando EL com Airbyte

Ao configurar source e destination no Airbyte, digite as credenciais com bastante atenção.

* Tendo instalado o Airbyte no Docker, é só abrir diretamente por ele:

![Image](https://github.com/user-attachments/assets/c6ee6cb7-003e-4fc2-9e9a-9cfe3b07cb08)

* Após, conecte o PostgreSQL no source e o Snowflake no destination:

![Image](https://github.com/user-attachments/assets/b008d9ab-0348-46b8-b860-d865abe4c479)

![Image](https://github.com/user-attachments/assets/a459ed7c-17b8-460a-82c8-f500e381be0c)

![Image](https://github.com/user-attachments/assets/b43d94ff-0781-4888-9f56-657629714c2c)

* Resultado no Snowflake:

![Image](https://github.com/user-attachments/assets/b7d33cf2-5c8d-4232-9e66-756e2d22b8c5)

Com isso feito iremos mandar a execução atravez do DBT.

A validação e garantia de qualidade de dados são processos críticos para assegurar que os dados utilizados em sistemas, análises e decisões sejam precisos, consistentes, completos e confiáveis.

Validação de Dados: Consiste em verificar a conformidade dos dados com regras, padrões e formatos predefinidos. Essa etapa identifica problemas como dados duplicados, valores ausentes, inconsistências entre fontes, erros de tipo ou violações de integridade referencial. A validação pode ocorrer em diferentes estágios, desde a extração até o carregamento no Data Warehouse.

Garantia de Qualidade de Dados: Envolve práticas e processos contínuos para manter e monitorar a qualidade dos dados ao longo de seu ciclo de vida. Isso inclui estabelecer métricas de qualidade, automatizar auditorias, corrigir problemas identificados, rastrear a origem dos dados (linhagem de dados) e implementar governança para assegurar que os dados permaneçam úteis e confiáveis.

Esses processos são fundamentais para evitar erros em análises, aumentar a confiança nos insights gerados e melhorar a tomada de decisão baseada em dados.

📚 Instalar DBT no Docker (arquivo Dockerfine no pasta)

![Image](https://github.com/user-attachments/assets/79712f07-354a-43a9-9653-0f5c8234438b)

* No container do DBT iniciamos com "dbt init projetodsa" e com isso fazer a configuração do conector (Snoeflake)

![Image](https://github.com/user-attachments/assets/9b27951c-7413-42a7-949e-9048d9e97125)

Estando configurado, agora é só transferir os modelos que estou fornecendo e colocar na pasta "models" que foi criada. Feito isso, volte para o Docker e execute dbt debug. Se tudo estiver configurado corretamente, o DBT estará conectado com o Snowflake.

![Image](https://github.com/user-attachments/assets/32b9cc0f-546f-4baf-b3f2-12f5798f4860)

* Antes de executar o dbt run, passe o arquivo YAML que estarei fornecendo para a pasta "projetodsa".

![Image](https://github.com/user-attachments/assets/a3a9e260-5c1b-43be-a012-e83fd6c20315)

📚 Modelos de Dados com DBT e SQL

São representações de tabelas ou visualizações em um banco de dados, criados a partir de arquivos SQL que aplicam transformações nos dados. Eles permitem organizar, documentar e padronizar a lógica de negócios e análises em um projeto. Os modelos geralmente são definidos como arquivos .sql, onde cada arquivo corresponde a uma tabela ou visualização no banco de dados.

* Agora, com tudo pronto, é só iniciar no Docker, na pasta do projeto, com dbt run, e ele irá iniciar os modelos:

![Image](https://github.com/user-attachments/assets/dfd15dee-f66a-40fa-aa9c-755e7f646bb4)

Com isso as tabelas dimenção foram para o Snowflake e a tabela fato:

![Image](https://github.com/user-attachments/assets/a32b927b-9e3e-4a24-acff-07ec9a3c2fd1)

📚 Verificando a linhagem dos dados no Snowflake

É o rastreamento da origem, movimentação, transformação e uso dos dados ao longo do tempo. Em outras palavras, é a capacidade de entender de onde os dados vêm, como foram processados, quem os utilizou e para quais finalidades. Essa prática é essencial para garantir a qualidade, confiabilidade e transparência dos dados em um sistema ou organização.

![Image](https://github.com/user-attachments/assets/77964450-bdb1-4096-98a3-f07a75f5c688)

📚 Orquestração e Automação

Na  plataforma  Snowflake,  orquestração  e  automação  referem-se  ao  gerenciamento  e execução  de  tarefas  e  processos  de  forma  integrada  e  eficiente,  permitindo  que  pipelines  de dados sejam executados automaticamente com mínima intervenção manual.

Orquestração:  Envolve  a  coordenação  de  processos,  como  extração,  transformação  e carregamento (ETL/ELT), para garantir que as tarefas sejam executadas na ordem correta e de maneira  otimizada.  Snowflake  oferece  integração  com  ferramentas  de  orquestração,  como Apache Airflow e dbt, para gerenciar fluxos de trabalho complexos.

Automação:  Permite  configurar  processos  recorrentes  e  monitorar eventos  dentro  da plataforma.  Snowflake  oferece  funcionalidades  como  Tasks  (tarefas  agendadas  que  executam consultas  SQL  ou  scripts),  Streams  (rastreio  de  alterações  em  dados)  e  Procedures  (blocos  de código SQL para lógica complexa), que juntos permitem criar pipelines de dados automatizados.

📚 Monitoramento e Alertas

No  Snowflake,  as  opções  de  monitoramento  e  alertas  são  projetadas  para  garantir  a visibilidade, desempenho e segurança dos ambientes de dados. As principais opções incluem:

1. Query  History:  Ferramenta  que  permite  monitorar  o  desempenho  e  o  histórico  de execução de consultas, ajudando na identificação de gargalos e otimização.

2. Resource  Monitors:  Permitem  acompanhar  e  gerenciar  o  uso  de  créditos  e  recursos computacionais. É possível configurar limites e criar alertas para evitar excessos de custos.

3. Account  Usage  Views:  Coleção  de  visualizações  que  oferecem  dados  detalhados  sobre atividades no ambiente, como uso de armazenamento, consultas e alterações de estrutura.

4. Integration   with   External   Tools:   Integração   com   ferramentas   de   monitoramento externas, como Datadog e Splunk, para alertas mais avançados e centralizados.

5. Alerts with Snowflake Tasks and Procedures: Combinando tarefas agendadas, streams e procedures, é possível configurar alertas customizados baseados em condições específicas, como falhas de processos ou anomalias de dados.

Essas  funcionalidades  ajudam  a garantir  a  operação  contínua  e  eficiente  do  Snowflake, além de suportar práticas de governança e controle de custos

