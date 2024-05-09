## Sumário
Estrutura do documento
Cenário/Declaração do problema
Visão geral do relatório do Power BI Desktop
  - Tarefa 1: Configurar o Power BI Desktop no ambiente de laboratório
  - Tarefa 2: Analisar relatório do Power BI Desktop
  - Tarefa 3: Revisar Power Queries
Referências

## Estrutura do documento
O laboratório inclui etapas a serem seguidas pelo usuário juntamente com as capturas de tela associadas que fornecem auxílio visual. Em cada captura de tela, as seções estão destacadas com caixas laranjas para indicar as áreas nas quais o usuário deve se concentrar.
## Cenário/Declaração do problema
A Fabrikam, Inc. é distribuidora atacadista de produtos inovadores. Como atacadista, os clientes da Fabrikam são principalmente empresas que revendem para pessoas físicas. A Fabrikam vende para clientes de varejo nos Estados Unidos, incluindo lojas especializadas, supermercados, lojas de informática e lojas de atrações turísticas. A Fabrikam também vende para outros atacadistas por meio de uma rede de agentes que promovem os produtos em nome da Fabrikam. Embora todos
os clientes da Fabrikam estejam atualmente nos Estados Unidos, a empresa pretende impulsionar a expansão para outros países/regiões.

Você é um Analista de Dados na equipe de Vendas. Você coleta, limpa e interpreta conjuntos de dados para resolver problemas de negócios. Você também reúne visualizações, como tabelas e gráficos, escreve relatórios e os apresenta aos tomadores de decisão na organização.

Para obter insights valiosos dos dados, você extrai dados de vários sistemas, limpa-os e combina-os. Você extrai dados das seguintes fontes:
  - **Dados de Venda:** são obtidos do sistema ERP e armazenados em um banco de dados ADLS Gen2 ou Databricks. Eles são atualizados ao meio-dia/12h, todos os dias.
  - **Dados do Fornecedor:** são obtidos de diferentes fornecedores e armazenados em um banco de dados Snowflake. São atualizados à meia-noite/24h, todos os dias.
  - **Dados do Cliente:** são obtidos do Customer Insights e armazenados no Dataverse. Os dados estão sempre atualizados.
  - **Dados do Funcionário:** são obtidos do sistema de RH e armazenados como um arquivo de exportação em uma pasta do SharePoint. São atualizados todas as manhãs, às 9h.
![](../Images/lab-01/image01.png)
No momento, você está criando um conjunto de dados no Power BI Premium que extrai os dados dos sistemas de origem acima para que você possa gerar relatórios e fornecer aos usuários finais o recurso de autoatendimento. Você usa o Power Query para atualizar seu modelo.

### Você está enfrentando os seguintes desafios:
  - Você precisa atualizar seu conjunto de dados pelo menos três vezes por dia para acomodar os diferentes horários de atualização para as diferentes fontes de dados.
  - As atualizações podem demorar, pois é sempre necessário fazer uma atualização completa para capturar tudo o que foi atualizado nos sistemas de origem.
  - Os erros detectados em qualquer uma das fontes das quais você está extraindo dados
resultarão na interrupção da atualização do conjunto de dados. Muitas vezes o arquivo do funcionário não é carregado no prazo, resultando na interrupção da atualização do conjunto de dados.
  - As alterações no modelo de dados demoram muito tempo, pois o Power Query leva tempo para atualizar as versões preliminares devido aos tamanhos de dados grandes e às
transformações complexas.
  - Você precisa de um computador com Windows para usar o Power BI Desktop mesmo que o padrão corporativo seja Mac.

Você ouviu falar do Microsoft Fabric e decidiu tentar ver se ele resolverá seus desafios.
## Visão geral do relatório do Power BI Desktop
Antes de começarmos com o Fabric, vamos dar uma olhada no Relatório atual no Power BI Desktop para entender as transformações e o modelo.
### Tarefa 1: Configurar o Power BI Desktop no ambiente de laboratório
1.	Abra o arquivo **FAIAD.pbix** que está na pasta **C:\FAIAD\Reports** do seu ambiente de laboratório. O arquivo será aberto no Power BI Desktop.
![](../Images/lab-01/image02.png)
2.	Insira seu endereço de email na caixa de diálogo aberta. Navegue até a guia **Environment Details**.
no painel direito do ambiente de laboratório.
3.	Copie os dados de **Username** e cole na caixa de texto Email da caixa de diálogo.
4.	Selecione **Continue**.
![](../Images/lab-01/image03.png)
5.	A caixa de diálogo Vamos entrar é aberta. Selecione **Conta corporativa ou de estudante.**
6.	Selecione **Continuar.**
![](../Images/lab-01/image04.png)
7.	A caixa de diálogo Sign in é aberta. Insira novamente os dados de **Username** copiando-os da guia **Environment Details.**
8.	Selecione **Next**.
![](../Images/lab-01/image05.png)