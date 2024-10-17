# Microsoft Fabric - Fabric Analyst in a Day - 实验 3 	 

![](../media/lab-03/image000.png) 

# 目录
- 简介	
- ADLS Gen2 的快捷方式	
	- 任务 1：创建快捷方式	
- 使用视觉对象查询转换数据	
	- 任务 2：使用视觉对象查询创建 Geo 视图	
	- 任务 3：使用视觉对象查询创建 Reseller 视图	
	- 任务 4：使用视觉对象查询创建 Sales 视图	
	- 任务 5：使用视觉对象查询创建 Product 视图	
- 参考	

# 简介
在我们的应用场景中，销售数据来自 ERP 系统，存储在 ADLS Gen2 中。每天中午 12 点更新。我们需要将此数据转换并引入到湖屋中，并在我们的模型中使用此数据。

可通过多种方法引入此数据。

- **快捷方式：** 这将创建指向数据的链接，我们可以使用视觉对象查询视图来转换它。我们将在本实验室中使用快捷方式。
- **笔记本：** 这需要我们编写代码。这种方法适合开发人员。
- **数据流 Gen2：** 您可能熟悉 Power Query 或数据流 Gen1。数据流 Gen2 顾名思义是数据流的新版本。它提供 Power Query/数据流 Gen1 的所有功能，并添加了将数据转换和引入到多个数据源的功能。我们将在下面几个实验室中进行介绍。
- **数据管道：** 这是一个编排工具。可以编排活动来提取、转换和引入数据。我们将使用数据管道执行数据流 Gen2 活动，该活动又将执行提取、转换和引入。

我们将首先创建一个快捷方式，以将数据从 ADLS Gen2 数据源引入到湖屋中。引入后，我们将使用视觉对象查询视图来转换它。

在本实验室结束时，您将了解到：

- 如何创建湖屋的快捷方式

- 如何使用视觉对象查询转换数据

# ADLS Gen2 的快捷方式

# 任务 1：创建快捷方式

快捷方式用于创建指向目标位置的链接。这就像在 Windows 桌面中创建快捷方式一样。

1. 让我们导航回您在实验室 2 任务 9 中创建的 **Fabric 工作区。**
2. 如果您在上一个实验室之后尚未导航离开，您将位于湖屋屏幕中。如果您已导航离开，没有关系。选择 **lh_FAIAD** 以导航到湖屋。
 
3. 在**资源管理器**面板中，选择**表**旁边的**省略号。**
 
4. 选择**新建快捷方式。**

   ![](../media/lab-03/image006.jpg) 

5. **新建快捷方式**对话框随即打开。在**外部源**下，选择 **Azure Data Lake Storage Gen2。**

   ![](../media/lab-03/image009.jpg) 

6. 您需要建立與 ADLS Gen2 資料來源的連線。在“連接設定”->“URL”下輸入此連結 `https://stvnextblobstorage.dfs.core.windows.net/fabrikam-sales`

7. 從「驗證類型」下拉清單中選擇「**共用存取簽章 (SAS)**」。

8. 從 **環境變數** 標籤（「實驗室指南」標籤旁）複製 **SAS 令牌**，並將其貼上到 **SAS 令牌** 方塊中。

9. 選擇螢幕右下角的**下一步**。

   ![](../../english/media/lab-03/image012.jpg) 

10. 您将连接到 ADLS Gen2，目录结构显示在左侧面板中。展开 **Delta-Parquet-Format-F Y25。**
11. **选择**以下目录：

	a.	Application.Cities

	b.	Application.Countries

	c.	Application.StateProvinces

	d.	DateDim

	e.	Sales.BuyingGroups

	f.	Sales.Customers

	g.	Sales.Invoices

	h.	Sales.InvoiceLines

	i.	Warehouse.StockItems

	j.	Warehouse.StockGroups

	k.	Warehouse.StockItemStockGroups

	**注意：** Sales.Invoices_May 是唯**一未**选择的目录。
 
12. 选择**下一步。**

	![](../media/lab-03/image015.png) 

13. 系统会将您的导航到下一个对话框，我们可以在其中编辑名称。针对 **Application.Citie s，** 在“操作”下选择**编辑图标。**

14. 将 **Application.Cities 重命名为 Cities。**

15. 选中名称旁边的复选标记以保存更改。

	![](../media/lab-03/image018.jpg) 
 
16. 同样，按如下所示重命名快捷方式名称：

	a. 将 Application.Countries 重命名为 **Countries**

	b. 将 Application.StateProvinces 重命名为 **States**

	c. 将 DateDim 重命名为 **Date**

	d. 将 Sales.BuyingGroups 重命名为 **BuyingGroups**

	e. 将 Sales.Customers 重命名为 **Customers**

	f. 将 Sales.InvoiceLines 重命名为 **InvoiceLineItems**

	g. 将 Sales.Invoices 重命名为 ***Invoices**

	h. 将 Warehouse.StockGroups 重命名为 **ProductGroups**

	i. 将 Warehouse.StockItemStockGroups 重命名为 **ProductItemGroup**

	j. 将 Warehouse.StockItems 重命名为 **ProductItem**

	**注意：** 仔细检查名称。拼写错误可能会导致实验室期间出现错误。

17. 选择**创建**以创建快捷方式。

	![](../media/lab-03/image021.jpg) 
 
18. 请注意，所有快捷方式均以表的形式创建。选择 **BuyingGroups** 表，请注意，我们可以看到数据面板中的数据预览。

	![](../media/lab-03/image024.png) 

	下一步是转换数据，我们可以创建语义模型。我们将创建视图以转换数据。

# 使用视觉对象查询转换数据

## 任务 2：使用视觉对象查询创建 Geo 视图

1. 我们可以使用 SQL 终结点访问湖屋。这提供查询数据和创建视图的功能。在屏幕的**右上角，** 选择**湖屋 -> SQL 分析终结点。**

	![](../media/lab-03/image027.jpg) 

	系统会将您导航到 SQL 分析终结点。请注意，“资源管理器”面板已更改。现在，您可以创建视图、存储过程、查询等。我们将创建一个可提供类似于界面的 Power Query 的视觉对象查询，并将其另存为视图。
 
	我们将首先创建 Geo 视图。我们需要合并 Cities、States 和 Countries 查询的数据来创建 G eo。

2. 从顶部菜单中，选择**新建视觉对象查询。**

	![](../media/lab-03/image030.jpg) 

3. 我们需要将表拖动到“视觉对象查询”面板来生成查询。将 Cities、States 和 Countries查询拖动到“视觉对象查询”面板中。

	![](../media/lab-03/image033.png)  
 
	我们需要合并这些查询。视觉对象查询附带使用 Power Query 编辑器的选项。让我们来使用此选项，因为我们对此很熟悉。

4. 从视觉对象查询编辑器的菜单中，选择**焦点模式**图标（位于右侧）。系统会将您导航到 Po wer Query 编辑器。

	![](../media/lab-03/image036.png) 

5. 选择 Cities 查询后，从 Power Query 编辑器功能区中，选择**主页 -> 合并查询 -> 将查询合并为新查询。** “合并查询”对话框随即打开。

	![](../media/lab-03/image039.jpg)  
 
6. 在**用于合并的左表**中，选择 **Cities。**
7. 在**用于合并的右表**中，选择 **States。**
8. 从两个表中选择 **StateProvinceID** 列。我们将使用此列进行联接。
9. 选择**内部**作为**联接种类。**
 
10. 选择**确定。**

	![](../media/lab-03/image042.jpg) 

	请注意，已创建名为“Merge”的新查询。我们需要“States”中的几列。

11. 在**数据视图**（底部面板）中，单击 **States** 列（右侧最后一列）旁边的**双箭头。**
12. 面板随即打开。**选择**以下列：

	a.	StateProvinceCode

	b.	StateProvinceName

	c.	CountryID

	d.	SalesTerritory
 
13. 选择**确定。**

	![](../media/lab-03/image045.jpg) 

	现在，我们需要合并 Countries 查询。

14. 选择 Merge 查询后，从功能区中选择**主页 -> 合并查询 -> 合并查询。**

	![](../media/lab-03/image048.jpg) 

15. “Merge 查询”对话框随即打开。在**用于合并的右表**中，选择 **Countries。**
16. 从两个表中选择 **CountryID** 列。我们将使用此列进行联接。
17. 选择**内部**作为**联接种类。**
 
18. 选择**确定。**

	![](../media/lab-03/image051.jpg) 

	我们需要“Countries”中的几列。

19. 在**数据视图**（底部面板）中，单击 **Countries** 列旁边的**双箭头。**
20. 面板随即打开。**选择**以下列：

	a.	CountryName

	b.	FormalName

	c.	IsoAlpha3Code

	d.	IsoNumericCode

	e.	CountryType

	f.	Continent

	g.	Region

	h.	Subregion

21. 选择**确定。**

	![](../media/lab-03/image054.jpg)  
 
	我们不需要所有列。让我们仅选择所需列。

22. 选择 Merge 查询后，从功能区中选择**主页 -> 选择列 -> 选择列。**

	![](../media/lab-03/image057.jpg) 

23. “选择列”对话框随即打开。**取消选中**以下列。

	a.	StateProvinceID

	b.	Location

	c.	LastEditedBy

	d.	ValidFrom

	e.	ValidTo

	f.	CountryID

24. 选择**确定。**
 
	![](../media/lab-03/image060.png) 

	请注意，该流程与 Power Query 类似，我们将所有步骤记录在右侧“已应用步骤”面板中和视觉对象视图中。让我们重命名 Merge 查询和启用加载，以便从此查询中加载数据。

25. 右键单击查询（左侧）面板中的 **Merge** 查询。选择**重命名**并将查询重命名为 **Geo。**
26. 右键单击查询（左侧）面板中的 **Geo** 查询。选择**启用加载**以启用此查询。
27. 确保 Cities、States 和 Countries 查询**已禁用。**
28. 选择**保存。**

	![](../media/lab-03/image063.jpg) 

	系统会将我们导航到视觉对象查询编辑器。现在，让我们将此查询另存为视图。

	**注意：** 我们使用 Power Query 编辑器执行的所有步骤也可以使用视觉对象查询编辑器执行。
29. 从“视觉对象查询编辑器”菜单中，选择**另存为视图。**
 
	![](../media/lab-03/image066.jpg) 

	“另存为视图”对话框随即打开。请注意，SQL 查询可用。您可以通过选择它来进行查看。
30. 输入 **Geo** 作为**视图名称。**
 
31. 选择**确定**以保存视图。

	![](../media/lab-03/image069.png) 

	保存视图后，您将收到警报。

32. 在资源管理器（左侧）面板中，展开**视图。** 我们有新创建的 Geo 视图。

	![](../media/lab-03/image072.png) 
 
## 任务 3：使用视觉对象查询创建 Reseller 视图

让我们创建 Reseller 视图，该视图可通过合并“Customers”表与“BuyingGroups”表来创建。这次我们将使用视觉对象查询创建视图。

1. 从湖屋菜单栏中，选择**主页 -> 新建视觉对象查询。** “新建视觉对象查询”随即打开。
2. 从“资源管理器”部分中，将“Customers”和“BuyingGroups”表拖动到视觉对象查询部分。

	![](../media/lab-03/image075.png) 

3. 选择 **Customers** 查询。选择后，“Customers”将有一个蓝色边框，“表”后面有一个 “+”号（这指示我们要在“表”后面添加一个步骤。如果您在“表”后没有看到“+”号，则可能选择了其他步骤。选择“表”即可开始）。
4. 从“视觉对象查询”菜单中，选择**组合 -> 合并查询。**

	![](../media/lab-03/image078.png) 

	“合并”对话框随即打开，其中已选择“Customers”作为顶部表。
5. 在**用于合并的右表**中，选择 **BuyingGroups。**
6. 从两个表中选择 **BuyingGroupID** 列。我们将使用此列进行联接。
7. 选择**内部**作为**联接种类。**
 
8. 选择**确定。**

	![](../media/lab-03/image081.png) 

9. 在**数据视图**（底部面板）中，单击 **BuyingGroups** 列旁边的**双箭头**（右侧最后一列）以从 BuyingGroups 中选择所需的列。
10. 面板随即打开。**选择 BuyingGroupName** 列。
11. 选择**确定。**

	![](../media/lab-03/image084.jpg) 

	我们不需要所有列。让我们仅选择所需列。
 
12. 从“视觉对象查询”菜单中，选择**管理列 -> 选择列。**

	![](../media/lab-03/image087.png) 

13. “选择列”对话框随即打开。**选择**以下列。

	a.	ResellerID

	b.	ResellerName

	c.	PostalCityID

	d.	PhoneNumber

	e.	FaxNumber

	f.	WebsiteURL

	g.	DeliveryAddressLine1

	h.	DeliveryAddressLine2

	i.	DeliveryPostalCode

	j.	PostalAddressLine1

	k.	PostalAddressLine2

	l.	PostalPostalCode

	m.	BuyingGroupName

14. 选择**确定。**

	![](../media/lab-03/image090.png) 
 
15. 让我们重命名“BuyingGroupName”列。在**数据**视图中，双击“BuyingGroupName”列标头以使其可编辑。
 
16. 将此列**重命名**为 **ResellerCompany。**

	![](../media/lab-03/image093.jpg) 

	请注意，“Customer”表已记录所有步骤。现在，让我们保存此视图。

17. 从“视觉对象查询”菜单中，选择**另存为视图。**

	![](../media/lab-03/image096.png) 

	“另存为视图”对话框随即打开。请注意，SQL 查询可用。您可以通过选择它来进行查看。
18. 输入 **Reseller** 作为**视图名称。**
19. 选择**确定**以保存视图。

	![](../media/lab-03/image099.png) 

	保存视图后，您将收到警报。

20. 在资源管理器（左侧）面板中，展开**视图。** 我们有新创建的 Reseller 视图。

	![](../media/lab-03/image102.png) 

## 任务 4：使用视觉对象查询创建 Sales 视图
让我们创建 Sales 视图，该视图可通过合并“InvoiceLineItems”和“Invoices”表与“Res eller”视图来创建。我们在 Power BI Desktop 中有此查询。我们将从“高级编辑器”复制代码。但在复制代码之前，我们需要使用视觉对象查询创建一个合并表，因为无法在视觉对象查询中创建空白查询。让我们试一下此方法。

1. 从湖屋菜单栏中，选择**主页 -> 新建视觉对象查询。**“新建视觉对象查询”随即打开。
2. 从**资源管理器 -> 表**部分中，将 **InvoiceLineItems、Invoices** 表拖动到视觉对象查询部分
3. 从**资源管理器 -> 视图**部分中，将 **Reseller** 视图拖动到视觉对象查询部分
 
4. 在视觉对象查询编辑器中，选择**焦点模式图标**以打开 Power Query 编辑器。

	![](../media/lab-03/image105.jpg) 

5. 选择 InvoiceLineItems 查询后，从功能区中选择**主页 -> 合并查询 -> 将查询合并为新查询。**

	![](../media/lab-03/image108.jpg) 

	“合并”对话框随即打开。

6. 在**用于合并的左表**中，选择 **InvoiceLineItems。**
7. 在**用于合并的右表**中，选择 **Invoices。**
8. 从两个表中选择 **InvoiceID** 列。我们将使用此列进行联接。
9. 选择**内部**作为**联接种类。**
 
10. 选择**确定。**

	![](../media/lab-03/image111.jpg) 

	我们将从 Power BI Desktop 中复制代码并使用“高级编辑器”粘贴它。

11. 如果您尚未打开 **FAIAD.pbix，** 请打开它。它位于您的实验室环境的桌面的 **Reports** 文件夹中。

12. 从功能区中选择**主页 -> 转换数据。** Power Query 窗口随即打开。您在之前的实验室中注意到，左侧面板中的查询是按数据源组织的。

	![](../media/lab-03/image114.jpg) 
 
13. 在左侧面板的“ADLSData”文件夹下，选择 **Sales** 查询。
14. 从功能区中选择**主页 -> 高级编辑器。** “高级编辑器”对话框随即打开。

	![](../media/lab-03/image117.png) 

15. **选择第 3 行中的代码** (#"Expanded Invoice" …) 一直到最后一行代码。
16. **右键单击**并选择**复制。**
17. 选择**取消**以关闭“高级编辑器”。

	![](../media/lab-03/image120.jpg) 

18. **导航回已打开 Power Query 编辑器的浏览器。**
19. 确保您已选择 **Merge** 查询。
 
20. 从功能区中选择**主页 -> 高级编辑器。** “高级编辑器”对话框随即打开。

	![](../media/lab-03/image123.jpg) 

21. 在**第 2 行的末尾添加逗号** (Source = Table.NestedJoin(InvoiceLineItems, {"InvoiceID "}, Invoices, {"InvoiceID"}, "Invoices", JoinKind.Inner)
22. 单击 **Enter** 以开始一个新行。
23. 在键盘上按 **Ctrl+V** 以粘贴从 Power BI Desktop 复制的代码。

	**注意：** 如果您在实验室环境中工作，请选择屏幕右上角的省略号。使用滑块**启用 VM 本机剪贴板。** 在对话框中选择“确定”。粘贴查询后，您可以禁用此选项。

	![](../media/lab-03/image126.jpg) 

24. 突出显示最后两行代码（在源中），然后将其**删除**。
 
25. 选择**确定**以保存更改。

	![](../media/lab-03/image129.jpg) 

	为了更方便起见，请删除“高级编辑器”中的所有代码，并将以下代码粘贴到“高级编辑器”中。

    ```
    let
    Source = Table.NestedJoin(InvoiceLineItems, {"InvoiceID"}, Invoices, {"InvoiceID"}, "Invoices", JoinKind.Inner),
    #"Expanded Invoice" = Table.ExpandTableColumn(Source, "Invoices", {"CustomerID",
    "BillToCustomerID", "SalespersonPersonID", "InvoiceDate"}, {"CustomerID", "BillToCustomerID", "SalespersonPersonID", "InvoiceDate"}),
    #"Removed Other Columns" = Table.SelectColumns(#"Expanded Invoice",{"InvoiceLineID", "InvoiceID", "StockItemID", "Quantity", "UnitPrice", "TaxRate", "TaxAmount", "LineProfit", "ExtendedPrice", "CustomerID", "SalespersonPersonID", "InvoiceDate"}),
    #"Renamed Columns" = Table.RenameColumns(#"Removed Other Columns",{{"CustomerID", "ResellerID"}}),
    
    #"Merged Queries" = Table.NestedJoin(#"Renamed Columns", {"ResellerID"}, Reseller,
    {"ResellerID"}, "Customer", JoinKind.Inner),
    #"Added Custom" = Table.AddColumn(#"Merged Queries", "Sales Amount", each [ExtendedPrice] - [TaxAmount]),
    #"Changed Type" = Table.TransformColumnTypes(#"Added Custom",{{"Sales Amount", type number}}),
    #"Removed Columns" = Table.RemoveColumns(#"Changed Type",{"Customer"}) in
    #"Removed Columns"
    ```

26. 系统会将您导航回 Power Query 编辑器。在左侧的“查询”面板中，双击 **Merge** 查询以对其重命名。
27. **将** Merge 查询重命名为 **Sales。**
 
28. 右键单击“Sales”查询，然后选择**启用加载**以启用要加载的查询。

	![](../media/lab-03/image132.png) 

29. 选择**保存**以保存并关闭 Power Query 对话框。系统会将您导航到视觉对象查询。
30. 从“视觉对象查询”菜单中，选择**另存为视图。** “另存为视图”对话框随即打开。请注意，SQL 查询可用。您可以通过选择它来进行查看。
31. 输入 **Sales** 作为**视图名称。**
32. 选择**确定**以保存视图。

	![](../media/lab-03/image135.png) 

	保存视图后，您将收到警报。
 
33. 在资源管理器（左侧）面板中，展开**视图。** 我们有新创建的 Sales 视图。

	![](../media/lab-03/image138.jpg) 

## 任务 5：使用视觉对象查询创建 Product 视图
让我们创建 Product 视图，该视图可通过合并“ProductItem”、“ProductItemGroup”与 “ProductGroups”表来创建。若要继续，我们需要将代码复制到“高级编辑器”中。

1. 从湖屋菜单栏中，选择**主页 -> 新建视觉对象查询。** “新建视觉对象查询”随即打开。
2. 从“资源管理器”部分中，将 **ProductItem、ProductItemGroup 和 ProductGroups**
表拖动到视觉对象查询部分
 
3. 在视觉对象查询编辑器中，选择**焦点模式图标**以打开 Power Query 编辑器。

	![](../media/lab-03/image141.png) 

4. 选择 **ProductItem** 查询后，从功能区中选择**主页 -> 合并查询 -> 将查询合并为新查询。**

	“合并”对话框随即打开。

	![](../media/lab-03/image144.jpg) 	

5. 在**用于合并的左表**中，选择 **ProductItem。**
6. 在**用于合并的右表**中，选择 **ProductItemGroup。**
7. 从两个表中选择 **StockItemID** 列。我们将使用此列进行联接。
8. 选择**左外**作为**联接种类。**
 
9. 选择**确定。** 已创建新的“Merge”查询。

	![](../media/lab-03/image147.jpg) 

10. 选择 Merge 查询后，从功能区中，选择**主页 -> 高级编辑器。**“高级编辑器”对话框随即打开。

	![](../media/lab-03/image150.jpg) 

11. 在“高级编辑器”中**选择全部代码，** 然后将其**删除。**
12. 将以下代码**粘贴**到“高级编辑器”中。

    ```
    let
    Source = Table.NestedJoin(ProductItem, {"StockItemID"}, ProductItemGroup, {"StockItemID"}, "ProductItemGroup", JoinKind.LeftOuter),
    #"Expanded ProductItemGroup" = Table.ExpandTableColumn(Source, "ProductItemGroup",
    {"StockGroupID"}, {"StockGroupID"}),
    #"Merged queries" = Table.NestedJoin(#"Expanded ProductItemGroup", {"StockGroupID"}, ProductGroups, {"StockGroupID"}, "ProductGroups", JoinKind.LeftOuter),
    #"Expanded ProductGroups" = Table.ExpandTableColumn(#"Merged queries", "ProductGroups", {"StockGroupName"}, {"StockGroupName"}),
    
    #"Choose columns" = Table.SelectColumns(#"Expanded ProductGroups", {"StockItemID", "StockItemName", "SupplierID", "Size", "IsChillerStock", "TaxRate", "UnitPrice",
    "RecommendedRetailPrice", "TypicalWeightPerUnit", "StockGroupName"})
    in
    #"Choose columns"
    ```
 
13. 选择**确定**以关闭“高级编辑器”。系统会将您导航回 Power Query 编辑器。

	![](../media/lab-03/image161.jpg) 

14. 在左侧的“查询”面板中，双击 **Merge** 查询以对其重命名。
15. **将** Merge 查询重命名为 **Product。**
16. 右键单击“Product”查询，然后选择**启用加载**以启用要加载的查询。
17. 选择**保存**以保存并关闭 Power Query 对话框。系统会将您导航到视觉对象查询。

	![](../media/lab-03/image164.jpg) 
 
18. 从“视觉对象查询”菜单中，选择**另存为视图。** “另存为视图”对话框随即打开。请注意，SQL 查询可用。您可以通过选择它来进行查看。
19. 输入 **Product** 作为**视图名称。**
 
20. 选择**确定**以保存视图。

	![](../media/lab-03/image167.png) 

	保存视图后，您将收到警报。

21. 在资源管理器（左侧）面板中，展开**视图。** 我们有新创建的 Product 视图。

	![](../media/lab-03/image170.jpg) 

	我们已转换来自 ADLS Gen2 数据源的数据。在本实验室中，我们了解了如何创建快捷方式，并探索了使用视觉对象查询视图转换数据的各种选项。

	在下一个实验室中，我们将了解如何使用数据流 Gen2 以及如何创建另一个湖屋的快捷方式。
 
# 参考
Fabric Analyst in a Day (FAIAD) 介绍了Microsoft Fabric 中提供的一些主要功能。在服务菜单中， “帮助 (?)”部分包含指向一些优质资源的链接。

![](../media/lab-03/image173.png)

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
