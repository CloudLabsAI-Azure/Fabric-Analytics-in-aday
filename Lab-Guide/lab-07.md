![](../Images/lab-07/lab7.png)

## 目录

- 简介

- Power BI

    - 任务 1：自动创建报表

    - 任务 2：为新报表配置背景

    - 任务 3：向报表中添加标头

    任务 4：向报表中添加KPI

    - 任务 5：向报表中添加折线图	

    - 任务 6：保存报表

    - 任务 7：配置 Date 表中的Year 列	

    - 任务 8：在Date 表中配置 Short_Month_Name 列	

    - 任务 9：设置折线图的格式

    - 任务 10：添加新数据以模拟 Direct Lake 模式

- 清理实验环境

- 参考	

 
## 简介

我们已将来自不同数据源的数据引入  Lakehouse，为数据源设置刷新计划并创建数据模型。我们接下来创建报表。

本实验结束后，您将学会：

- 如何自动创建报表

- 如何从空白画布开始生成报表

- 如何体验 Direct Lake 模式以自动刷新数据

## Power BI

### 任务 1：自动创建报表

我们先使用自动创建报表选项。稍后在实验中，我们将重新创建Power BI 中的报表。

1.	我们导航回到您在之前的实验中创建的 **Fabric 工作区。**

2.	在左侧面板底部，选择 **Fabric 体验选择器**图标。

3.	Fabric 体验对话框随即打开。选择 **Power BI**。您将导航到 **Power BI 主页**。

![](../Images/lab-07/image1.png)
 
4.	从顶部菜单中选**择新建报告**。

![](../Images/lab-07/image2.png)

5.	您将导航到**生成第一个报表屏幕** 可以选择手动输入数据并生成报表，或选择已发布的语 义模型。我们在之前的实验中创建了一个语义模型。我们来使用该模型。选择**选择发布的 语义模型**选项。

![](../Images/lab-07/image3.jpg)


6.	“选择要在报表中使用的语义模型”页面随即打开。请注意，我们有四个选项。选择 **lh_FAIAD：**

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;a.**lh_FAIAD**：这是  Lakehouse，其中包含我们创建并希望用于报表的数据集。

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;b.**Units by Supplier**：这是我们使用T-SQL 创建的数据集。

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;c.**DataflowsStagingWarehouse**：这是默认创建的暂存仓库。由于我们没有暂存数据， 因此我们没有使用它。

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;d.**DataflowsStagingLakehouse**：这是默认创建的暂存湖屋。由于我们没有暂存数据， 因此我们没有使用它。
 
7.	点击“**自动创建报表”按钮旁边的箭头**。请注意，有两个选项：“自动创建报表”和“创建空白报表”。我们来尝试自动创建报表，因此选择**自动创建报表**。

![](../Images/lab-07/image4.jpg)

8.	Power BI 将开始自动创建报表。请注意，您也可以选择此处的Pre-select data 选项。报表准备好后，屏幕右上角会出现一个对话框。选择 **View report now**。

![](../Images/lab-07/image5.jpg)

**检查点：**您将得到一份与下面的屏幕截图相似的报表。有一些 KPI 和一些趋势视觉图。如果您要分析新模型并需要快速启动，可以从这里入手。

**注意**：请注意，在顶部菜单上，您可以选择“编辑报表”或以表的形式查看某些数据。请随意 浏览这些选项。

9.	我们保存该报表。从顶部菜单中选择**保存**。
 
10.	“保存报表”对话框随即打开。将报表命名为 **rpt_Sales_Auto_Report
注意**：我们在报表名称前加上  rpt（报表的缩写）作为前缀。

11.	确保将报表保存在您的工作区 **FAIAD_<username>**。
12.	选择**保存**。

![](../Images/lab-07/image6.jpg)

**注意：**您看到的自动创建的报表可能有所不同，因为它是“自动创建的”。它还取决于您在上 一个实验（实验 6）中创建的关系和度量值。

如果您创建了所有关系和度量值（包括**可选**关系，实验 6），则上面的屏幕截图显示了自动创建的报表可能显示的样子。

如果您不创建**可选**关系和度量值（实验 6），则下面的屏幕截图显示了自动创建的报表可能显示的样子。

![](../Images/lab-07/image7.jpg)

 
## 任务 2：为新报表配置背景

我们使用空白画布创建新报表。

1.	在**左侧面板**中，选择您的工作区名称 **FAIAD_<username>** 以导航到该工作区。

2.	从顶部菜单中，选择**新建-> 报表**。您将导航到生成第一个报表页面。

![](../Images/lab-07/image8.png)

3.	选择**选择发布的语义模型**，这样就可以选择我们创建的模型。

![](../Images/lab-07/image9.jpg)

4.	“选择要在报表中使用的语义模型”对话框随即打开。选择 **lh_FAIAD**。

5.	点击“自动创建报表”**按钮旁边的箭头。**选择创**建空白报表**。
 
 ![](../Images/lab-07/image10.jpg)

6.	如果您还未打开**FAIAD.pbix**，请打开它。它位于您的实验环境的**C:\FAIAD\Reports** 文件夹中。

我们将使用这份报表作为参考。先添加画布背景。我们将创建报表标头，添加几个KPI，并创建随时间变化的销售额折线图。为了节省时间，并且鉴于您具有在Power BI Desktop 中生成视觉对象的经验，我们不会创建所有视觉对象。

![](../Images/lab-07/image11.jpg)

7.	在浏览器中导航到 **Power BI 画布**。

8.	在“可视化”窗格中，选择**设置页面格式图标。**

9.	展开**画布背景部分**。
 
10.	从**图像**选项中选择**浏览。**“文件资源管理器”对话框随即打开。

11.	导航到实验环境的 **C:\FAIAD\Reports** 文件夹。

12.	选择 **Summary Background.png**。

13.	将**图像匹配度下**拉菜单设置为**填充。**

14.	然后将“透明度”设置为 **0%。**

![](../Images/lab-07/image12.jpg)


### 任务 3：向报表中添加标头

1.	我们在上边距中添加标头。从**菜单**中选择**文本框**。

2.	在文本框的第一行输入 **Fabrikam Company**。

3.	在文本框的第二行输入 **Sales Report。**

4.	突出显示 **Fabrikam Company**，并将**字体**设置为 **Segoe UI**，**字体大小**设置为 **18，粗体。**

5.	突出显示 **Sales Report**，并将**字体**设置为 **Segoe UI**，**字体大小**设置为 **14**。

6.	**选中文本框**后，在右侧的“设置文本框格式”窗格中，**展开效果。**

7.	使用**背景**滑块将其设置为**关闭**。

8.	调整**文本框的大小以适合上边距**。

 ![](../Images/lab-07/image13.jpg)

### 任务 4：向报表中添加 KPI

1.	我们添加销售KPI。选择画布中的**空白区域**，以将焦点从文本框上移开。

2.	从**可视化部分**，选择多**行卡视觉对象**。

3.	从**数据部分**展开 **Sales 表。**

4.	选择 **Sales 度量**。

![](../Images/lab-07/image14.jpg)

5.	选择**多行卡视觉对象**后，从“可视化”部分选择**设置视觉对象格式图标**。

6.	展开**类别标签**部分。

7.	将**字体大小**增大到 **14**。

8.	选择**颜色下拉列表**。调色板对话框随即打开。

9.	将十六进制值设置为 **#004753。**
 
 ![](../Images/lab-07/image15.jpg)

10.	展开**卡**部分。

11.	使用**强调栏**滑块将其设置为**关闭**。
 
 ![](../Images/lab-07/image16.png)

12.	在“可视化”窗格中选择**常规**。

13.	展开**效果部分**。

14.	使用**背景**滑块将其设置为**关闭**。

15.	对**视觉对象**调整大小，并将其移到左**侧框，如屏幕截图所示**。

![](../Images/lab-07/image17.png)

16.	我们再添加一个KPI。选择我们刚刚创建的 **Sales 多行卡片**。通过从键盘中选择 **Ctrl+C** 来复制视觉对象。

17.	通过从键盘中选择 **Ctrl+V**  来**粘贴** 视觉对象。请注意，视觉对象已粘贴到画布上。

18.**突出显示新视觉对象** 后，在**可视化窗格-> 生成视觉对象-> 字段**部分删除 **Sales** 度量。
 
19.	从**数据**部分展开 **Sales** 表，并选择 **Units** 度量。

20.	对**视觉对象**调整大小，并将其**放置在Sales 视觉对象下方的框中。**

![](../Images/lab-07/image18.jpg)

### 任务 5：向报表中添加折线图

我们创建一个折线图来可视化经销商公司随时间变化的销售额。

1.	选择画布中的**空白区域**，以将焦点从多行卡片视觉对象上移开。

2.	在**可视化部分**中选择**折线图**。

3.	从**数据部分**展开 **Date** 表。

4.	选择 **Year** 字段。请注意，Year 默认为求和值并添加到Y 轴。我们来更正一下吧。

![](../Images/lab-07/image19.jpg)

 
### 任务 6：保存报表

在我们导航离开报表并对模型进行更改之前，我们先保存该报表。

1.	从顶部菜单中，选择 **文件-> 保存。**

2.	“保存报表”对话框随即打开。将报表命名为 **rpt_Sales_Report**
**注意：**我们在报表名称前加上  rpt（报表的缩写）作为前缀。

3.	确保将报表保存在 **FAIAD_<username>** 工作区。

4.	选择**保存。**

![](../Images/lab-07/image20.jpg)


### 任务 7：配置Date 表中的Year 列

1.	从**左侧菜单栏**中，选择 **lh_FAIAD** 以导航到湖屋。

2.	从左侧 Explorer 窗格中，展开 **lhFAIAD -> Schemas -> dbo -> Tables -> Date。**

3.	选择 **Year** 列。

4.	在右侧**属性**窗格中，展开**高级**部分。

5.	在**汇总依据**下拉列表中，选择**无**。

 ![](../Images/lab-07/image21.jpg)

6.	通过选择左侧菜单栏的 **rpt_Sales_Report**，导航回到报表。

7.	从顶部菜单中，选择**编辑**。

8.	从顶部菜单中选择**刷新**。请注意，在数据面板中，Year   不是求和字段。

9.	选择**折线图视觉对象**后，从 Y 轴**删除Year 的总和**。

10.	选择 **Year** 字段，它将添加到 **X 轴。**


11.	展开 **Sales** 表，并选择 **Sales 度量**。

![](../Images/lab-07/image22.jpg)

### 任务 8：在Date 表中配置Short_Month_Name 列

1.	我们向该图表添加月份。从 Date 表中，将 **Short_Month_Name** 字段拖到 **X 轴**中的 **Year 下**方。请注意，视觉对象是按 Sales 排序的。我们将其按 Short_Month_Name 排序。

2.	选择视觉对象右上角的**省略号 (…)。**

3.	选择**排列轴 -> Year Short_Month_Name。**

4.	选择视觉对象右上角的**省略号 (…)。**

5.	选择**排列轴 -> 以升序排序。**

![](../Images/lab-07/image23.jpg)

**注意**：月份按字母顺序排序。让我们来解决这个问题。
 
 ![](../Images/lab-07/image24.jpg)

6.	从**左侧菜单栏**中，选择 **lh_FAIAD** 以导航到湖屋。

7.	**更改尚未保存**对话框随即打开。选择**保存**，将更改**保存**到报表。

![](../Images/lab-07/image25.png)

8.	将会导航至lh_FAIAD lakehouse。从左侧 Explorer 窗格中，展开 **lhFAIAD -> Schemas -> dbo -> Tables -> Date。**

9.	选择 **Short_Month_Name** 列。

10.	在右侧**属性**窗格中，展开**高级**部分。

11.	在**按列排序**下拉列表中，选择 **Month。**

![](../Images/lab-07/image26.jpg)

12.	通过选择左侧菜单栏的 **rpt_Sales_Report**，导航回到报表。

13.	从顶部菜单中，选择**编辑。**

14.	从顶部菜单中选择**刷新**。请注意，现在月份已正确排序。
 
 ![](../Images/lab-07/image27.png)

### 任务 9：设置折线图的格式

请注意，在生成报表时，更新语义模型很容易。这实现了像 Power BI Desktop 一样的无缝交互。

1.	**选择折线图视觉对象**后，**在数据部分**，展开 **Reseller** 表。

2.	将 **Reseller -> Reseller Company** 字段拖到**图例**部分。

![](../Images/lab-07/image28.jpg)

3.	**选择折线图视觉对象**后，从**可视化**部分选择设**置视觉对象格式图标 ->  常规。**

4.	展开**标题**部分。

5.	将**标题**文本设置为 **Sales over time。**

6.	展开**效果**部分。

7.	使用**背景**滑块将其设置为**关闭**。
 
 ![](../Images/lab-07/image29.png)

8.	在可视化部分中，选择设**置视觉对象格式图标 -> 视觉对象**。

9.	展开**行**部分。

10.	展开**颜色**部分。

11.	将 **Wingtip Toys** 颜色设置为 **#004753**

12.	将 **Tailspin Toys** 颜色设置为 **#F17925**

13.	对**视觉对象**调整大小，并将其移到**右上方框，如屏幕截图所示**。

14.	滚动到视觉对象的右侧，**请注意，我们拥有截至 2023 年 4 月的数据**。

![](../Images/lab-07/image30.png)

15.	我们保存报表，从菜单中选择**文件-> 保存。**

如前所述，我们不会在本实验中生成所有视觉对象。如果您有时间，可以自行生成更多视觉 对象。
 
### 任务 10：添加新数据以模拟 Direct Lake 模式

在Import 模式下，刷新源中的数据后，我们通常需要刷新Power BI 模型，以更新报表中的数据。通过使用 Direct Query 模式，刷新源中的数据后，这些数据就可以在Power BI 报表中使用。然而，direct query 模式通常很慢。为了解决这个问题，Microsoft Fabric 引入了 Direct Lake 模式。Direct Lake 是一种将数据从湖中直接加载到Power BI 引擎中以供分析的快速路径。我们来探索一下。

在实际应用场景中，数据是在源进行更新的。由于我们处于训练环境中，因此我们在模拟时， 将其连接到包含 2023 年 5 月数据的 parquet 文件。

1.	在左侧菜单栏中，选择 **FAIAD_<username>**  以导航到工作区主页。
2.	选择 **df_Sales_ADFS**，以便我们可以通过添加新的 Parquet 文件来编辑数据流。

![](../Images/lab-07/image31.jpg)

3.	从功能区中选择**主页 -> 获取数据 -> 空白查询**。

4.	“连接到数据源”对话框随即打开。选择**编辑器中的所有行并删除它。**
 
5.	复制以下代码并将其粘贴到编辑器中。

```
let
Source = #"ADLS Base Folder",
#"Filtered Rows" = Table.SelectRows(Source, each Text.Contains([Folder Path], "Sales.Invoices_May")),

#"https://stvnextblobstorage dfs core windows net/fabrikam-sales/Delta-Parquet-Format/Sales Invoices_May/_0- 0ee085a3-716f-4833-a792-c3162c1de300-0 parquet" = #"Filtered Rows"{[#"Folder
Path"="https://stvnextblobstorage.dfs.core.windows.net/fabrikam-sales/Delta-Parquet-
Format/Sales.Invoices_May/",Name="0-0ee085a3-716f-4833-a792-c3162c1de300-0.parquet"]}[Content],

#"Imported Parquet" = Parquet.Document(#"https://stvnextblobstorage dfs core windows net/fabrikam-sales/Delta- Parquet-Format/Sales Invoices_May/_0-0ee085a3-716f-4833-a792-c3162c1de300-0 parquet")
in
#"Imported Parquet"
```

6.	选择**下一步**。
![](../Images/lab-07/image32.jpg)

7.	新查询已**重新创建**。现在我们对其重命名。在右侧面板中的**查询设置 -> 属性 -> 名称下**， 将查询重命名为 **MayInvoice。**

8.	我们现在禁用暂存新查询。**右键单击**“MayInvoice    查询”并**取消选中“启用暂存**”。

 ![](../Images/lab-07/image33.jpg)

9.	现在，我们将 5 月份的发票数据追加到Invoice 表中。从“查询”部分选择 **Invoice** 查询。

10.	在功能区中，选择**主页-> 追加**查询。

11.	“追加查询”对话框随即打开。从**要追加的表**下拉列表中，选择  **MayInvoice。**

12.	选择**确定。**

![](../Images/lab-07/image34.jpg)

13.	在右下角，选择**发布**以保存和发布更新。

![](../Images/lab-07/image35.jpg)

**注意**：发布后，数据流将刷新。这可能需要几分钟的时间。
 
14.	从左侧菜单栏选择 **rpt_Sales_Report**，以导航回到报表。

15.	从顶部菜单中选择**刷新**。请注意，折线图中现在有 2023 年 5 月的数据。此外还要注意， 销售额和单位数有所增加。

![](../Images/lab-07/image36.jpg)

当我们在之前的实验中创建的数据流按计划刷新时，数据就会被引入到 Lakehouse。Lakehouse 中的数据模型已更新，报表也已刷新。当每个数据流刷新时，我们不必刷新数据模型和报表。 这是 Direct Lake 的优点。

我们来回顾一下问题陈述中列出的挑战：

- **您每天要刷新数据集至少 3  次，以适应不同数据源的不同更新时间。**
我们使用 Direct Lake 解决了这个问题。每个单独的数据流都按计划刷新。数据集和报表无需刷新。

- **刷新需要很长时间，因为您每次都需要完全刷新，以捕获源系统中的所有更新。**
我们仍然使用 Direct Lake 解决了这个问题。每个单独的数据流都按计划刷新。数据集和报表无需刷新，因此我们无需执行完全刷新。

- **用于提取数据的任何数据源中一旦发生任何错误，都将导致数据集刷新中断。很多时 候，员工文件没有按时上传，导致数据集刷新中断。**
数据管道解决了这个问题，因为它能够在刷新失败时以不同时间间隔再次尝试刷新。

- **由于数据量大且转换复杂，对数据模型进行任何更改都需要很长时间，因为 Power Query 需要很长时间刷新预览。**
我们注意到，数据流不仅高效，而且方便更改。数据流中加载预览通常不需要很长 时间。

- **您需要使用 Windows PC 才能使用 Power BI Desktop，但企业标配的是 Mac**。
Microsoft Fabric 是一种 SaaS 产品/服务。我们只需要使用浏览器来访问该服务即可。无需在桌面上安装任何软件。
 

## 清理实验环境
准备好清理实验环境后，请按照以下步骤操作。

1.	从左侧面板中选择 FAIAD_<username> 工作区，以导航到工作区主页。
2.	从顶部菜单中，选择“管理访问权限”旁边的省**略号   (…)**，然后选择**工作区设置**。

![](../Images/lab-07/image37.jpg)

3.	“工作区设置”对话框随即打开。从左侧菜单中选择**其他**。

4.	选择**删除此工作区**。

5.	“删除工作区”对话框随即打开。选择**删除**。

这将删除工作区以及工作区中包含的所有项目。

![](../Images/lab-07/image38.jpg)
 
### 参考

Fabric Analyst in a Day (FAIAD) 介绍了Microsoft Fabric 中提供的一些主要功能。在服务菜单中， “帮助 (?)”部分包含指向一些优质资源的链接。

![](../Images/lab-04/image37.png)

以下更多参考资源可帮助您进行 Microsoft Fabric 相关的后续步骤。

- 请参阅博客文章以阅读完整的[Microsof t Fabric GA 公告](https://aka.ms/Fabric-Hero-Blog-Ignite23)

- 通过[引导式教程](https://aka.ms/Fabric-GuidedTour)探索 Fabric

- 注册 [Microsoft Fabric 免费试用版](https://aka.ms/try-fabric)

- 通过探索[Microsoft Fabric 网站](https://aka.ms/microsoft-fabric)

- 通过探索 [Fabric 学习模块](https://aka.ms/learn-fabric)学习新技能

- 探索 [Fabric 技术文档](https://aka.ms/fabric-docs)

- 阅读[有关Fabric 入门指南的免费电子书](https://aka.ms/fabric-get-started-ebook)

- 加入[Fabric 社区](https://aka.ms/fabric-community)发布问题、分享反馈并向他人学习

阅读更多深度Fabric 体验公告博客：

- [Fabric 中的Data Factory 体验博客](https://aka.ms/Fabric-Data-Factory-Blog)

- [Fabric 中的Synapse Data Engineering 体验博客](https://aka.ms/Fabric-DE-Blog)

- [Fabric 中的Synapse Data Science 体验博客](https://aka.ms/Fabric-DS-Blog)

- [Fabric 中的Synapse Data Warehousing 体验博客](https://aka.ms/Fabric-DW-Blog)

- [Fabric 中的Synapse Real-Time Analytics 体验博客](https://aka.ms/Fabric-RTA-Blog)

- [Power BI 公告博客](https://aka.ms/Fabric-PBI-Blog)

- [Fabric 中的Data Activator 博客](https://aka.ms/Fabric-DA-Blog)

- [Fabric 中的管理和治理博客](https://aka.ms/Fabric-Admin-Gov-Blog)

- [Fabric 中的OneLake 博客](https://aka.ms/Fabric-OneLake-Blog)

- [Dataverse 和Microsof t Fabric 集成博客](https://aka.ms/Dataverse-Fabric-Blog)

© 2023 Microsoft Corporation.保留所有权利。

© 2023 Microsoft Corporation.保留所有权利。使用此演示/实验即表示您已同意以下条款: 
本演示/实验中的技术/功能由 Microsoft Corporation 出于获取反馈和提供学习体验的目的提供。只能将本演示/实验用于评估这些技术特性和功能以及向Microsoft 提供反馈。不得用于任何其他用途。不得对此演示/实验或其任何部分进行修改、复制、分发、传送、显示、 执行、复制、公布、许可、转让、销售或基于以上内容创建衍生作品。
严禁将本演示/实验（或其任何部分）复制到任何其他服务器或位置以便进一步复制或再  分发。

本演示/实验出于上述目的，在不涉及复杂设置或安装操作的模拟环境中提供特定软件技术
/产品特性和功能，包括潜在的新功能和概念。本演示/实验中展示的技术/概念可能不是完 整的功能，可能会以不同于最终版本的工作方式工作。我们也可能不会发布此类功能或概念的最终版本。在物理环境中使用此类特性和功能的体验可能也有所不同。

**反馈**。如您针对本演示/实验中所述的技术特性、功能和/或概念向 Microsoft 提供反馈，则意味着您向Microsoft  无偿提供以任何方式、出于任何目的使用和分享您的反馈并将其商业化的权利。您同样无偿为第三方提供其产品、技术和服务使用或配合使用包含此反馈的
Microsoft 软件或服务的任何特定部分所需的任何专利权。如果根据某项许可的规定，
Microsoft  由于在其软件或文档中包含了您的反馈需要向第三方授予该软件或文档的许可， 请不要提供这样的反馈。这些权利在本协议终止后继续有效。
反馈。如您针对本演示/实验中所述的技术特性、功能和/或概念向 Microsoft 提供反馈，则意味着您向Microsoft  无偿提供以任何方式、出于任何目的使用和分享您的反馈并将其商业化的权利。您同样无偿为第三方提供其产品、技术和服务使用或配合使用包含此反馈的
Microsoft 软件或服务的任何特定部分所需的任何专利权。如果根据某项许可的规定，
Microsoft  由于在其软件或文档中包含了您的反馈需要向第三方授予该软件或文档的许可， 请不要提供这样的反馈。这些权利在本协议终止后继续有效。

对于本演示/实验，Microsoft Corporation 不提供任何明示、暗示或法定的保证和条件，包括有关适销性、针对特定目的的适用性、所有权和不侵权的所有保证和条件。对于使用本 演示/实验产生的结果或输出内容的准确性，或者出于任何目的包含本演示/实验中的信息的适用性，Microsoft 不做任何保证或陈述。

**免责声明**

本演示/实验仅包含 Microsoft Power BI 的部分新功能和增强功能。在产品的后续版本中， 部分功能可能有所更改。在本演示/实验中，可了解部分新功能，但并非全部新功能。
