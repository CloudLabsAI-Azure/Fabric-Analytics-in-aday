![](../Images/lab-02/image.png)

## Sumário
- Introdução	
- Licença do Fabric
  - Tarefa 1: Habilitar uma licença de avaliação do Microsoft Fabric	
- Visão geral das experiências do Fabric	<br>
  - Tarefa 2: Experiência do Data Factory<br>	
  - Tarefa 3: Experiência do Data Activator<br>	
  - Tarefa 4: Experiência do Industry Solutions<br>	
  - Tarefa 5: Experiência do Synapse Data Engineering	<br>
  - Tarefa 6: Experiência do Synapse Data Science	<br>
  - Tarefa 7: Experiência do Synapse Data Warehouse	<br>
  - Tarefa 8: Experiência do Real-Time Analytics	<br>
- Workspace do Fabric	<br>
  - Tarefa 9: Criar um workspace do Fabric	<br>
  - Tarefa 10: Criar um Lakehouse	<br>
- Referências	

## Introdução
Hoje você aprenderá sobre vários recursos importantes do Microsoft Fabric. Este é um workshop
introdutório destinado a apresentar as diversas experiências de produtos e os vários itens disponíveis no Fabric. Ao final deste workshop, você saberá como usar os recursos Lakehouse, Fluxo de Dados
Gen2, Pipeline de Dados e DirectLake.

Ao final deste laboratório, você terá aprendido:
  - Como criar um workspace do Fabric
  - Como criar um Lakehouse


## Licença do Fabric
### Tarefa 1: Habilitar uma licença de avaliação do Microsoft Fabric
1. Abra o **navegador** e acesse https://app.powerbi.com/. Você será direcionado para a página de logon.<br>
**Observação:** Se você não estiver usando o ambiente de laboratório e já tiver uma conta do Power BI, talvez queira usar o navegador no modo privado/anônimo.

2. Insira o **Nome de usuário** disponível na guia **Variáveis de Ambiente** (ao lado do Guia de Laboratório) como o **Email** e clique em **Enviar.**

   ![](../Images/lab-02/image01.png)

3. Você será direcionado à tela **Senha.** Insira a **Senha** disponível na guia **Variáveis de Ambiente**
(ao lado do Guia de Laboratório), que o instrutor compartilhou com você.
4. Clique em **Entrar** e siga as instruções para entrar no Fabric.

   ![](../Images/lab-02/image02.png)

5. Você será direcionado à conhecida **Página Inicial de Serviço do Power BI.**
6. Presumimos que você esteja familiarizado com o layout do Serviço do Power BI. Se você tiver alguma dúvida, não hesite em perguntar ao instrutor.

Atualmente, você está em **Meu workspace**. Para trabalhar com itens do Fabric, você precisará de uma licença de avaliação e de um workspace que tenha a licença do Fabric. Vamos configurar tudo.

7. No canto superior direito da tela, selecione o **ícone de usuário**.
8. Selecione **Start trial.**

   ![](../Images/lab-02/image03.png)

9. A caixa de diálogo Atualizar para uma avaliação gratuita do Microsoft Fabric é aberta. Selecione **Iniciar avaliação.**

   ![](../Images/lab-02/image04.png)
 
10. Selecione o **“X”** no canto superior direito da caixa de diálogo **Apenas uma última etapa** para fechá-la. Não forneceremos esses detalhes, pois se trata de um ambiente de laboratório.

   ![](../Images/lab-02/image05.png)

11. A caixa de diálogo Atualizado com êxito para o Microsoft Fabric é aberta. Selecione **Fabric Home Page**.

   ![](../Images/lab-02/image06.png)

12. Você será direcionado à **Página Inicial do Microsoft Fabric**.

    ![](../Images/lab-02/image07.png)

 
## Visão geral das experiências do Fabric
### Tarefa 2: Experiência do Data Factory
1. Selecione o ícone **Microsoft Fabric** (fabric experience selector) na parte inferior esquerda da tela. Uma caixa de diálogo com a lista de experiências do Fabric será aberta. Observe que o Power BI, o Data Factory, Data Activator e o Industry Solutions são experiências independentes. Data Engineering, Data Science, Data Warehouse e Real-Time Analytics são experiências do Synapse
e essas quatro experiências são da plataforma Synapse. Vamos explorar.
2. Selecione **Data Factory**.

   ![](../Images/lab-02/image08.png)

3. Você é direcionado para a **Página Inicial do Data Factory.** A página contém três seções principais.<br>
a. **New:** lista os itens disponíveis no Data Factory – Dataflow Gen2 e Data pipeline.<br>
&nbsp; &nbsp; &nbsp;i. Dataflow Gen2 é a próxima geração de Fluxo de Dados.<br>
&nbsp; &nbsp; &nbsp;ii. Data pipeline é usado para orquestração de dados.<br>
b. **Recommended:** esta seção fornece acesso à documentação de aprendizagem de início rápido.<br>
c. **Quick access:** esta seção lista os itens favoritos ou usados recentemente.

   ![](../Images/lab-02/image09.png)

 
### Tarefa 3: Experiência do Data Activator
1. Selecione o **ícone Fabric experience selector** (atualmente definido como Data Factory) na parte inferior esquerda da tela. A caixa de diálogo de experiência do Fabric é aberta.

   ![](../Images/lab-02/image10.png)

2. Selecione **Data Activator** na caixa de diálogo. Você será direcionado para a **Página Inicial do Data Activator.** O Data Activator é uma experiência no-code no Microsoft Fabric para executar ações automaticamente quando padrões ou condições são detectados em dados alterados. Observe que as três seções são como a experiência do Data Factory. Na seção Novo, observe os itens:<br>
&nbsp; &nbsp; &nbsp;a. **Reflex:** usado para monitorar conjuntos de dados, consultas e fluxos de eventos para padrões.<br>
&nbsp; &nbsp; &nbsp;b. **Exemplo do Reflex:** solução de exemplo.

   ![](../Images/lab-02/image11.png)

 
### Tarefa 4: Experiência do Industry Solutions
1. Selecione o **ícone Fabric experience selector** (atualmente definido como Data Activator) na parte inferior esquerda da tela. A caixa de diálogo de experiência do Fabric é aberta.
2. Selecione **Industry Solutions** na caixa de diálogo. Você será direcionado para a **Página Inicial do Industry Solutions.** O Microsoft Fabric oferece soluções de dados específicas do setor que
fornecem uma plataforma robusta para gerenciamento de dados, análise e tomada de decisões. Essas soluções de dados abordam os desafios exclusivos enfrentados por diferentes setores, permitindo que as empresas otimizem as operações, integrem dados de diferentes fontes e usem análises avançadas. Observe que as três seções são como as experiências anteriores. Na seção
Novo, observe os itens:

    **a.** **Soluções de sustentabilidade:** oferece suporte à ingestão, padronização e análise de dados de ESG (governança ambiental, social e corporativa).<br>
    **b.** **Soluções de varejo:** ajuda no gerenciamento de grandes volumes de dados, integrando dados de várias fontes e fornecendo análises em tempo real para tomada rápida de decisões. Os varejistas podem usar essas soluções para otimização de estoque, segmentação de clientes, previsão de vendas, preços dinâmicos e detecção de fraudes.

![](../Images/lab-02/image12.png)

### Tarefa 5: Experiência do Synapse Data Engineering
1. Selecione o **ícone Fabric experience selector** (atualmente definido como Industry Solutions) na parte inferior esquerda da tela. A caixa de diálogo de experiência do Fabric é aberta.
2. Selecione **Data Engineering**. Você será direcionado para a *Página Inicial do Data Engineering.* Novamente, a página contém três seções principais. Na seção New, observe os itens:<br>
a. **Lakehouse:** usado para armazenar Big Data para limpeza, consulta, geração de relatórios e compartilhamento.<br>
b. **Notebook:** usado para ingestão, preparação, análise e outras tarefas relacionadas a dados usando várias linguagens, como Python, R e Scala.<br>
c. **Environment:** usado para configurar bibliotecas compartilhadas, configurações de computação do Spark e recursos para notebooks e definições de trabalho do Spark.<br>
d. **Spark Job Definition:** usada para definir, agendar e gerenciar trabalhos do Apache.<br>
e. **Data pipeline:** usado para orquestrar a solução de dados.<br>
f. **Import notebook:** usado para importar notebooks da máquina local.<br>
g. **Use a sample:** solução de exemplo.

   ![](../Images/lab-02/image13.png)

 
### Tarefa 6: Experiência do Synapse Data Science
1. Selecione o **ícone Fabric experience selector** (atualmente definido como Data Engineering) na parte inferior esquerda da tela. A caixa de diálogo de experiência do Fabric é aberta.
2. Selecione **Data Science.** Você será direcionado para a **Página Inicial do Data Science.** Novamente, existem três seções. Na seção New, observe os itens:<br>
a. **ML model:** usado para criar modelos de machine learning.<br>
b. **Experiment:** usado para criar, executar e acompanhar o desenvolvimento de vários modelos.<br>
c. **Notebook:** usado para explorar dados e criar soluções de machine learning.<br>
d. **Environment:** usado para configurar bibliotecas compartilhadas, configurações de computação do Spark e recursos para notebooks e definições de trabalho do Spark.<br>
e. **Import notebook:** usado para importar notebooks da máquina local.<br>
f. Use a sample: solução de exemplo.

**Observação:** itens como Notebook, Environmente, Data pipeline estão disponíveis em várias experiências, pois são relevantes em cada uma dessas experiências.

   ![](../Images/lab-02/image14.png)
 
### Tarefa 7: Experiência do Synapse Data Warehouse
1. Selecione o **ícone Fabric experience selector** (atualmente definido como Data Science) na parte inferior esquerda da tela. A caixa de diálogo de experiência do Fabric é aberta.
2. Selecione **Data Warehouse**. Você será direcionado para a **Página Inicial do Data Warehouse.** Novamente, existem três seções. Na seção Novo, observe os itens:<br>
a. **Warehouse:** usado para criar um Data Warehouse.<br>
b. **Pipeline de dados:** usado para orquestrar a solução de dados.

   ![](../Images/lab-02/image15.png)
 
### Tarefa 8: Experiência do Real-Time Analytics
1. Selecione o **ícone Fabric experience selector** (atualmente definido como Data Warehouse) na parte inferior esquerda da tela. A caixa de diálogo de experiência do Fabric é aberta.
2. Selecione **Real-Time Analytics.** Você será direcionado para a **Página Inicial do Real-Time Analytics.** Novamente, existem três seções. Na seção Novo, observe os itens:<br>
a. **Eventhouse:** usado para criar um workspace de banco de dados, que pode ser compartilhado entre projetos.<br>
b. **Banco de Dados KQL:** usado para carregar rapidamente dados e armazenar dados estruturados, não estruturados e de streaming para consulta.<br>
c. **Conjunto de Consultas KQL:** usado para executar consultas nos dados para produzir tabelas e visuais compartilháveis.<br>
d. **Eventstream:** usado para capturar, transformar e rotear fluxo de eventos em tempo real.<br>
e. **Usar uma amostra:** solução de exemplo.

   ![](../Images/lab-02/image16.png)

 
## Workspace do Fabric
### Tarefa 9: Criar um workspace do Fabric
1. Agora vamos criar um workspace com a licença do Fabric. Selecione **Workspaces** na barra de navegação esquerda. Uma caixa de diálogo é aberta.
2. Selecione **Novo workspace**.

   ![](../Images/lab-02/image17.png)

3. A caixa de diálogo **Criar um workspace** é aberta no lado direito do navegador.
4. No campo **Nome**, insira **FAIAD_<nome de usuário>.**

**Observação:** O nome do workspace deve ser exclusivo. No entanto, o nome do seu workspace deve ser diferente. Verifique se há uma marca de seleção verde em "Este nome está disponível", abaixo do campo Nome.

5. Se preferir, você pode inserir uma **Descrição** para o workspace. Esse campo é opcional.
6. Clique em **Avançado** para expandir a seção.

   ![](../Images/lab-02/image18.png)
    
7. Em **License mode**, verifique se **Trial** está selecionada. (Essa opção deve estar selecionada por padrão.)
8. Selecione **Apply** para criar um novo workspace.

   ![](../Images/lab-02/image19.png)


Um novo workspace é criado e você será direcionado para ele. Traremos dados de diferentes fontes de dados para o Lakehouse e usaremos os dados do Lakehouse para criar nosso modelo e relatá-lo. A primeira etapa é criar um Lakehouse.
 
### Tarefa 10: Criar um Lakehouse
1. Selecione o **ícone Fabric experience selector** (atualmente definido como Real-Time Analytics) na parte inferior esquerda da tela. A caixa de diálogo de experiência do Fabric é aberta.
2. Selecione **Data Engineering** para ser direcionado para a Página Inicial do Data Engineering.

   ![](../Images/lab-02/image20.png)

3. Selecione **Lakehouse**.

   ![](../Images/lab-02/image21.png)

4. A caixa de diálogo New lakehouse é aberta. Digite **lh_FAIAD** na caixa de texto Nome.

    **Observação:** "lh" aqui se refere a Lakehouse. Estamos usando o prefixo "lh" para facilitar a identificação e a pesquisa.
5. Selecione **Create.**

   ![](../Images/lab-02/image22.png)

 
Em alguns instantes, um Lakehouse será criado e você será direcionado para a interface do Lakehouse. No **painel esquerdo**, observe que abaixo do seu workspace você terá o ícone Lakehouse. Você pode navegar facilmente até o Lakehouse clicando neste ícone a qualquer momento.

No explorador do Lakehouse, você observará **Tables** e **Files**. O Lakehouse poderá expor arquivos do Azure Data Lake Storage Gen2 na seção de arquivos, ou um fluxo de dados poderá carregar dados para as tabelas do Lakehouse. Existem várias opções disponíveis. Mostraremos algumas das opções nos laboratórios a seguir.

   ![](../Images/lab-02/image23.png)

Neste laboratório, exploramos a interface do Fabric, criamos um workspace do Fabric e um Lakehouse. No próximo laboratório, aprenderemos como usar o Fluxo de Dados Gen2 para se conectar ao ADLS Gen2 para extrair, transformar e ingerir dados no Lakehouse.
 
## Referências
O Fabric Analyst in a Day (FAIAD) apresenta algumas das principais funções disponíveis no Microsoft Fabric. No menu do serviço, a seção Ajuda (?) tem links para ótimos recursos.

   ![](../Images/lab-02/image24.png)

Veja aqui mais alguns recursos que ajudarão você com as próximas etapas do Microsoft Fabric.
  - Veja a postagem do blog para ler o [anúncio completo de GA do Microsoft Fabric](https://aka.ms/Fabric-Hero-Blog-Ignite23)
  - Explore o Fabric por meio do [Tour Guiado](https://aka.ms/Fabric-GuidedTour)
  - Inscreva-se para a [avaliação gratuita do Microsoft Fabric](https://aka.ms/try-fabric)
  - Visite o [site do Microsoft Fabric](https://aka.ms/microsoft-fabric)
  - Aprenda novas habilidades explorando os [módulos de Aprendizagem do Fabric](https://aka.ms/learn-fabric)
  - Explore a [documentação técnica do Fabric](https://aka.ms/fabric-docs)
  - Leia o [livro eletrônico gratuito sobre como começar a usar o Fabric](https://aka.ms/fabric-get-started-ebook)
  - Participe da [comunidade do Fabric](https://aka.ms/fabric-community) para postar suas perguntas, compartilhar seus comentários e aprender com outras pessoas

Leia os blogs de comunicados de experiências do Fabric em mais detalhes:
  - [Experiência do Data Factory no blog do Fabric](https://aka.ms/Fabric-Data-Factory-Blog)
  - [Experiência do Synapse Data Engineering no blog do Fabric](https://aka.ms/Fabric-DE-Blog)
  - [Experiência do Synapse Data Science no blog do Fabric](https://aka.ms/Fabric-DS-Blog)
  - [Experiência do Synapse Data Warehousing no blog do Fabric](https://aka.ms/Fabric-DW-Blog)
  - [Experiência do Synapse Real-Time Analytics no blog do Fabric](https://aka.ms/Fabric-RTA-Blog)
  - [Blog de comunicado do Power BI](https://aka.ms/Fabric-PBI-Blog)
  - [Experiência do Data Activator no blog do Fabric](https://aka.ms/Fabric-DA-Blog)
  - [Administração e governança no blog do Fabric](https://aka.ms/Fabric-Admin-Gov-Blog)
  - [OneLake no blog do Fabric](https://aka.ms/Fabric-OneLake-Blog)
  - [Blog de integração do Dataverse e Microsoft Fabric](https://aka.ms/Dataverse-Fabric-Blog)

  © 2023 Microsoft Corporation. Todos os direitos reservados.

Ao usar esta demonstração/este laboratório, você concorda com os seguintes termos:

A tecnologia/funcionalidade descrita nesta demonstração/neste laboratório é fornecida pela
Microsoft Corporation para obter seus comentários e oferecer uma experiência de aprendizado.
Você pode usar a demonstração/o laboratório somente para avaliar tais funcionalidades e
recursos de tecnologia e fornecer comentários à Microsoft. Você não pode usá-los para nenhuma outra finalidade. Você não pode modificar, copiar, distribuir, transmitir, exibir, executar,
reproduzir, publicar, licenciar, criar obras derivadas, transferir nem vender esta demonstração/este laboratório ou qualquer parte deles.

A CÓPIA OU A REPRODUÇÃO DA DEMONSTRAÇÃO/DO LABORATÓRIO (OU DE QUALQUER PARTE DELES) EM QUALQUER OUTRO SERVIDOR OU LOCAL PARA REPRODUÇÃO OU REDISTRIBUIÇÃO ADICIONAL É EXPRESSAMENTE PROIBIDA.

ESTA DEMONSTRAÇÃO/ESTE LABORATÓRIO FORNECE DETERMINADOS RECURSOS E
FUNCIONALIDADES DE PRODUTO/TECNOLOGIA DE SOFTWARE, INCLUINDO NOVOS RECURSOS E CONCEITOS POTENCIAIS, EM UM AMBIENTE SIMULADO SEM CONFIGURAÇÃO NEM
INSTALAÇÃO COMPLEXA PARA A FINALIDADE DESCRITA ACIMA. A TECNOLOGIA/OS CONCEITOS REPRESENTADOS NESTA DEMONSTRAÇÃO/NESTE LABORATÓRIO PODEM NÃO REPRESENTAR A
FUNCIONALIDADE COMPLETA DOS RECURSOS E PODEM NÃO FUNCIONAR DA MESMA MANEIRA QUE UMA VERSÃO FINAL. ALÉM DISSO, PODEMOS NÃO LANÇAR UMA VERSÃO FINAL DE TAIS RECURSOS OU CONCEITOS. SUA EXPERIÊNCIA COM O USO DE TAIS RECURSOS E
FUNCIONALIDADES EM UM AMBIENTE FÍSICO TAMBÉM PODE SER DIFERENTE.

**COMENTÁRIOS.** Caso você forneça comentários sobre os recursos de tecnologia, as funcionalidades e/ou os conceitos descritos nesta demonstração/neste laboratório à Microsoft, você concederá à Microsoft, sem encargos, o direito de usar, compartilhar e comercializar seus comentários de qualquer forma e para qualquer finalidade. Você também concede a terceiros, sem encargos, quaisquer direitos de patente necessários para que seus produtos, suas tecnologias e seus serviços usem ou interajam com partes específicas de um software ou um
serviço da Microsoft que inclua os comentários. Você não fornecerá comentários que estejam sujeitos a uma licença que exija que a Microsoft licencie seu software ou sua documentação para terceiros em virtude da inclusão de seus comentários neles. Esses direitos continuarão em vigor após o término do contrato.

POR MEIO DESTE, A MICROSOFT CORPORATION SE ISENTA DE TODAS AS GARANTIAS E CONDIÇÕES REFERENTES À DEMONSTRAÇÃO/AO LABORATÓRIO, INCLUINDO TODAS AS
GARANTIAS E CONDIÇÕES DE COMERCIALIZAÇÃO, SEJAM ELAS EXPRESSAS, IMPLÍCITAS OU ESTATUTÁRIAS, E DE ADEQUAÇÃO A UMA FINALIDADE ESPECÍFICA, TÍTULO E NÃO VIOLAÇÃO.
A MICROSOFT NÃO DECLARA NEM GARANTE A PRECISÃO DOS RESULTADOS DERIVADOS DO USO DA DEMONSTRAÇÃO/DO LABORATÓRIO NEM A ADEQUAÇÃO DAS INFORMAÇÕES CONTIDAS NA DEMONSTRAÇÃO/NO LABORATÓRIO A QUALQUER FINALIDADE.

**AVISO DE ISENÇÃO DE RESPONSABILIDADE**

Esta demonstração/este laboratório contém apenas uma parte dos novos recursos e aprimoramentos do Microsoft Power BI. Alguns dos recursos podem ser alterados em versões futuras do produto. Nesta demonstração/neste laboratório, você aprenderá sobre alguns dos novos recursos, mas não todos.
