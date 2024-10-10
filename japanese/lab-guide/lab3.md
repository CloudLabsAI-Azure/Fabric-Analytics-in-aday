目次
概要	3
ADLS Gen2 へのショートカット	4
タスク 1: ショートカットを作成する	4
ビジュアル クエリを使用してデータを変換する	9
タスク 2: ビジュアル クエリを使用して Geo ビューを作成する	9
タスク 3: ビジュアル クエリを使用して Reseller ビューを作成する	18
タスク 4: ビジュアル クエリを使用して Sales ビューを作成する	24
タスク 5: ビジュアル クエリを使用して Product ビューを作成する	31
参考資料	37




概要 

このシナリオでは、ERP システムから取得された販売データが ADLS Gen2 に格納されています。毎日正午 (午後 12 時) に更新されます。このデータを変換してレイクハウスに取り込み、モデルで使用する必要があります。 

このデータは複数の方法で取り込むことができます。 

ショートカット: データへのリンクが作成されます。ビジュアル クエリ ビューを使用して、データを変換できます。このラボではショートカットを使用します。 

Notebooks: この方法ではコードを記述する必要があります。これは、開発者にとって使いやすい方法です。 

データフロー (Gen2) を使用する。Power Query や データフロー (Gen1) についてはおそらくなじみがあることと思います。データフロー (Gen2) はその名前が示すように、新しいバージョンの データフローです。Power Query と データフロー (Gen1) のすべての機能に加え、データを変換して複数のデータ ソースに取り込む機能が追加されています。これについては以降のラボで紹介します。 

データ パイプラインを使用する。データ パイプラインはオーケストレーション ツールです。アクティビティに調整を加え、データを抽出、変換して取り込むことができます。ここではデータ パイプラインを使用してデータフロー (Gen2) のアクティビティを実行し、抽出、変換、取り込みを行います。 

まず、ショートカットを作成して、ADLS Gen2 データ ソースからレイクハウスにデータを取り込みます。データを取り込んだら、ビジュアル クエリ ビューを使用して、データを変換します。 

このラボを終了すると、次のことが学べます。 

レイクハウスへのショートカットの作成方法 

ビジュアル クエリを使用したデータの変換方法 

ADLS Gen2 へのショートカット 

タスク 1: ショートカットを作成する 

ショートカットは、ターゲットとなる場所へのリンクを作成するために使用されます。これは、Windows デスクトップでのショートカットの作成に似ています。 

ラボ 2 のタスク 9 で作成した Fabric ワークスペースに戻ります。 

前のラボの終了後に別の場所に移動していない場合は、レイクハウスの画面が表示されています。別の場所に移動した場合でも問題ありません。lh_FAIAD を選択して、レイクハウスに移動します。 

エクスプローラー パネルで、Tables の横にある省略記号を選択します。 

新しいショートカットを選択します。 

 

新しいショートカット ダイアログが開きます。外部ソースで、Azure Data Lake Storage Gen2 を選択します。 

 

ADLS Gen2 データ ソースへの接続を作成する必要があります。接続設定 -> URL に、リンク https://stvnextblobstorage.dfs.core.windows.net/fabrikam-sales を入力します。 

[認証の種類] ドロップダウンから、アカウント キーを選択します。 

環境変数タブ ([ラボ ガイド] タブの横) から ADLS ストレージ アカウントのアクセス キーをコピーし、アカウント キー テキスト ボックスに貼り付けます。 

画面右下の次へを選択します。 

 

ADLS Gen2 に接続され、左パネルにディレクトリ構造が表示されます。Delta-Parquet-Format-FY25 を展開します。 

次のディレクトリを選択します。 

Application.Cities 

Application.Countries 

Application.StateProvinces 

DateDim 

Sales.BuyingGroups 

Sales.Customers 

Sales.Invoices 

Sales.InvoiceLines 

Warehouse.StockItems 

Warehouse.StockGroups 

Warehouse.StockItemStockGroups 

注: Sales.Invoices_May だけが、選択されないディレクトリです。 

次へを選択します。 

 

名前を編集できる次のダイアログが表示されます。 Application.Cities の [アクション] の下にある編集アイコンを選択します。 

名前を Application.Cities から Cities に変更します。 

名前の横にあるチェック マークを選択して、変更を保存します。 

 

同様に、ショートカット名を次のように変更します。 

Application.Countries から Countries へ 

Application.StateProvinces から States へ 

DateDim から Date へ 

Sales.BuyingGroups から BuyingGroups へ 

Sales.Customers から Customers へ 

Sales.InvoiceLines から InvoiceLineItems へ 

Sales.Invoices から Invoices へ 

Warehouse.StockGroups から ProductGroups へ 

Warehouse.StockItemStockGroups から ProductItemGroup へ 

Warehouse.StockItems から ProductItem へ 

注: 名前をもう一度確認してください。入力ミスがあると、ラボでエラーが発生する可能性があります。 

作成を選択して、ショートカットを作成します。 

 

すべてのショートカットがテーブルとして作成されていることに注意してください。BuyingGroups テーブルを選択し、データ パネルにデータのプレビューが表示されることを確認してください。 

 

次の手順では、セマンティック モデルを作成するために、データを変換します。データを変換するためのビューを作成します。 

ビジュアル クエリを使用してデータを変換する 

タスク 2: ビジュアル クエリを使用して Geo ビューを作成する 

SQL エンドポイントを使用して、レイクハウスにアクセスできます。これにより、データに対するクエリの実行や、ビューの作成が可能になります。画面の右上で、レイクハウス -> SQL 分析エンドポイントを選択します。 

 

SQL 分析エンドポイントが表示されます。[エクスプローラー]パネルが変更されていることを確認してください。ビュー、ストアド プロシージャ、クエリなどを作成することができます。ここでは、Power Query のようなインターフェイスを提供するビジュアル・クエリを作成し、これをビューとして保存します。 

最初に、Geo ビューを作成します。Geo を作成するには、Cities、States、Countries の各クエリからのデータをマージする必要があります。 

上部のメニューから新規のビジュアル クエリを選択します。 

 

クエリを作成するには、テーブルを [ビジュアル クエリ] パネルにドラッグする必要があります。Cities、States、Countries の各クエリを [ビジュアル クエリ] パネルにドラッグしてください。 

 

これらのクエリをマージする必要があります。また、ビジュアル クエリには、Power Query エディターを使用するためのオプションがあります。このエディターに慣れているので、これを使用しましょう。 

ビジュアル クエリ エディターのメニューからフォーカス モード アイコンを選択します (右側にあります)。Power Query エディターが表示されます。 

 

Cities クエリを選択した状態で、Power Query エディターのリボンからホーム -> クエリのマージ -> 新規としてクエリをマージを選択します。[マージ] ダイアログが開きます。 

 

マージ用の左テーブルで Cities を選択します。 

マージ用の右テーブルで States を選択します。 

両方のテーブルから StateProvinceID 列を選択します。この列を使用して結合を実行します。 

結合の種類として内部を選択します。 

OK を選択します。 

 

マージという名前の新しいクエリが作成されたことを確認してください。States の列がいくつか必要になります。 

データ ビュー (下部のパネル) で、States 列 (右端の列) の横にある二重矢印をクリックします。 

パネルが開きます。次の列を選択します。 

StateProvinceCode 

StateProvinceName 

CountryID 

SalesTerritory 

OK を選択します。 

 

次に、Countries クエリをマージする必要があります。 

マージクエリを選択した状態で、リボンから ホーム - > クエリのマージ -> クエリのマージを選択します。 

 

[マージ] クエリ ダイアログが開きます。マージ用の右テーブルで Countries を選択します。 

両方のテーブルから CountryID 列を選択します。この列を使用して結合を実行します。 

結合の種類として内部を選択します。 

OK を選択します。 

 

Countries の列がいくつか必要になります。 

データ ビュー (下部のパネル) で、Countries 列の横にある二重矢印をクリックします。 

パネルが開きます。次の列を選択します。 

CountryName 

FormalName 

IsoAlpha3Code 

IsoNumericCode 

CountryType 

Continent 

Region 

Subregion 

OK を選択します。 

 

すべての列が必要になるわけではありません。必要な列だけを選択してください。 

マージクエリを選択した状態で、リボンから ホーム - > 列の選択 -> 列の選択を選択します。 

 

 

[列の選択] ダイアログが開きます。次の列をオフにします。 

StateProvinceID 

Location 

LastEditedBy 

ValidFrom 

ValidTo 

CountryID 

OK を選択します。 

 

プロセスは Power Query と類似しており、すべてのステップが、右側の [適用されたステップ] パネルとビジュアル ビューの両方に記録されていることを確認してください。Merge クエリの名前を変更し、読み込みを有効にして、このクエリからデータを読み込みましょう。 

[クエリ] パネル (左) で、マージクエリを右クリックします。名前の変更を選択し、クエリの名前を Geo に変更します。 

[クエリ] パネル (左) で、Geo クエリを右クリックします。読み込みを有効にするを選択し、このクエリを有効にします。 

Cities、States、Countries の各クエリが無効になっていることを確認してください。 

保存を選択します。 

 

ビジュアル クエリ エディターが表示されます。ここでは、このクエリをビューとして保存します。 

注: Power Query エディターを使用して実行したすべてのステップは、ビジュアル クエリ エディターを使用して実行することもできます。 

ビジュアル クエリ エディターのメニューからビューとして保存を選択します。 

 

[ビューとして保存] ダイアログが開きます。SQL クエリが使用可能になっていることに注目してください。選択すれば、そのクエリを確認することができます。 

ビュー名に Geo と入力します。 

OK を選択してビューを保存します。 

 

ビューが保存されると、アラートが表示されます。 

[エクスプローラー]パネル (左) で、Views を展開します。新しく作成された Geo ビューがあります。 

 

タスク 3: ビジュアル クエリを使用して Reseller ビューを作成する 

Customers テーブルと BuyingGroups テーブルをマージして、Reseller ビューを作成しましょう。今回は、ビジュアル クエリを使用してビューを作成します。 

レイクハウスのメニュー バーからホーム -> 新規のビジュアル クエリを選択します。新しいビジュアル クエリが開きます。 

[エクスプローラー] セクションから、Customers テーブルと BuyingGroups テーブルを [ビジュアル クエリ] セクションにドラッグします。 

 

Customers クエリを選択します。選択すると、Customers の周りに青の境界線が表示され、テーブルの後に "+" 記号が表示されます (これは、テーブルの後にステップを追加することを示しています。テーブルの後に "+" 記号が表示されない場合は、別のステップを選択している可能性があります。[テーブル] を選択すれば、続行できます)。 

ビジュアル クエリのメニューから結合 -> クエリのマージを選択します。 

 

[マージ] ダイアログが開き、Customers が最上位のテーブルとして選択されています。 

マージ用の右テーブルで BuyingGroups を選択します。 

両方のテーブルから BuyingGroupID 列を選択します。この列を使用して結合を実行します。 

結合の種類として内部を選択します。 

OK を選択します。 

 

データ ビュー (下部のパネル) で、BuyingGroups 列 (右端の列) の横にある二重矢印をクリックして、BuyingGroups から必要な列を選択します。 

パネルが開きます。BuyingGroupName 列を選択します。 

OK を選択します。 

  

すべての列が必要になるわけではありません。必要な列だけを選択してください。 

ビジュアル クエリのメニューから列の管理 -> 列の選択を選択します。 

 

 

[列の選択] ダイアログが開きます。次の列を選択します。 

ResellerID 

ResellerName 

PostalCityID 

PhoneNumber 

FaxNumber 

WebsiteURL 

DeliveryAddressLine1 

DeliveryAddressLine2 

DeliveryPostalCode 

PostalAddressLine1 

PostalAddressLine2 

PostalPostalCode 

BuyingGroupName 

OK を選択します。 

 

BuyingGroupName 列の名前を変更しましょう。データ ビューで BuyingGroupName 列ヘッダーをダブルクリックして、編集可能にします。 

列を ResellerCompany という名前に変更します。 

 

Customer テーブルには、すべてのステップが記録されていることを確認してください。次に、このビューを保存しましょう。 

ビジュアル クエリ エディターのメニューからビューとして保存を選択します。 

 

[ビューとして保存] ダイアログが開きます。SQL クエリが使用可能になっていることに注目してください。選択すれば、そのクエリを確認することができます。 

ビュー名に Reseller と入力します。 

OK を選択してビューを保存します。 

 

ビューが保存されると、アラートが表示されます。 

[エクスプローラー]パネル (左) で、Views を展開します。新しく作成された Reseller ビューがあります。 

 

タスク 4: ビジュアル クエリを使用して Sales ビューを作成する 

InvoiceLineItems テーブルと Invoices テーブル、および Reseller ビューをマージして、Sales ビューを作成しましょう。このクエリは Power BI Desktop にあります。詳細エディターからコードをコピーします。ただし、コードをコピーする前に、ビジュアル クエリを使用してマージ テーブルを作成する必要があります。これは、ビジュアル クエリでは空のクエリを作成できないためです。この方法を試してみましょう。 

レイクハウスのメニュー バーからホーム -> 新規のビジュアル クエリを選択します。新しいビジュアル クエリが開きます。 

エクスプローラー -> Tables セクションから、InvoiceLineItems と Invoices の各テーブルを [ビジュアル クエリ] セクションにドラッグします。 

エクスプローラー -> Views セクションから、Reseller ビューを [ビジュアル クエリ] セクションにドラッグします。 

ビジュアル クエリ エディターで、フォーカス モード アイコンを選択して Power Query エディターを開きます。 

 

InvoiceLineItems クエリを選択した状態で、リボンからホーム -> クエリのマージ -> 新規としてクエリをマージを選択します。 

 

[マージ] ダイアログボックスが開きます。 

マージ用の左テーブルで InvoiceLineItems を選択します。 

マージ用の右テーブルで Invoices を選択します。 

両方のテーブルから InvoiceID 列を選択します。この列を使用して結合を実行します。 

結合の種類として内部を選択します。 

OK を選択します。 

 

Power BI Desktop からコードをコピーし、詳細エディターを使用して、これを貼り付けます。 

まだ開いていない場合は、お使いのラボ環境のデスクトップにある Reports フォルダー内の FAIAD.pbix を開きます。 

リボンからホーム -> データの変換を選択します。Power Query ウィンドウが開きます。前のラボで確認したように、左パネルのクエリはデータ ソースごとに整理されています。 

 

左パネルの ADLSData フォルダーにある Sales クエリを選択します。 

リボンからホーム -> 詳細エディターを選択します。[詳細エディター] ダイアログが開きます。 

 

3 行目 (#"Expanded Invoice" …) から最後のコード行までのコードを選択します。 

右クリックしてコピーを選択します。 

キャンセルを選択して詳細エディターを閉じます。 

 

Power Query エディターが開いているブラウザーに戻ります。 

マージクエリが選択されていることを確認してください。 

リボンからホーム -> 詳細エディターを選択します。[詳細エディター] ダイアログが開きます。 

 

2 行目 (Source = Table.NestedJoin(InvoiceLineItems, {"InvoiceID"}, Invoices, {"InvoiceID"}, "Invoices", JoinKind.Inner) の末尾にコンマを追加します。 

Enter を押して、新しい行を開始します。 

キーボードで Ctrl+V を押して、Power BI Desktop からコピーしたコードを貼り付けます。 

注: ラボ環境で作業している場合は、画面の右側にある省略記号を選択してください。スライダーを使用して VM ネイティブ クリップボードを有効にします。ダイアログで [OK] を選択します。クエリの貼り付けが済んだら、このオプションを無効にしてかまいません。 

 

コードの最後の 2 行 (ソース内) を強調表示して削除します。 

OK をクリックして変更を保存します。 

 

簡単に行うには、詳細エディターですべてのコードを削除し、次のコードを詳細エディターに貼り付けます。 

let 

  Source = Table.NestedJoin(InvoiceLineItems, {"InvoiceID"}, Invoices, {"InvoiceID"}, "Invoices", JoinKind.Inner), 

    #"Expanded Invoice" = Table.ExpandTableColumn(Source, "Invoices", {"CustomerID", "BillToCustomerID", "SalespersonPersonID", "InvoiceDate"}, {"CustomerID", "BillToCustomerID", "SalespersonPersonID", "InvoiceDate"}), 

    #"Removed Other Columns" = Table.SelectColumns(#"Expanded Invoice",{"InvoiceLineID", "InvoiceID", "StockItemID", "Quantity", "UnitPrice", "TaxRate", "TaxAmount", "LineProfit", "ExtendedPrice", "CustomerID", "SalespersonPersonID", "InvoiceDate"}), 

    #"Renamed Columns" = Table.RenameColumns(#"Removed Other Columns",{{"CustomerID", "ResellerID"}}), 

    #"Merged Queries" = Table.NestedJoin(#"Renamed Columns", {"ResellerID"}, Reseller, {"ResellerID"}, "Customer", JoinKind.Inner), 

    #"Added Custom" = Table.AddColumn(#"Merged Queries", "Sales Amount", each [ExtendedPrice] - [TaxAmount]), 

    #"Changed Type" = Table.TransformColumnTypes(#"Added Custom",{{"Sales Amount", type number}}), 

    #"Removed Columns" = Table.RemoveColumns(#"Changed Type",{"Customer"}) 

in 

    #"Removed Columns" 

 

Power Query エディターに戻ります。左側の [クエリ] パネルで、マージクエリをダブルクリックして、名前を変更します。 

Merge クエリを Sales という名前に変更します。 

Sales クエリを右クリックし、読み込みを有効にするを選択して、クエリが読み込まれるようにします。 

 

保存を選択してクエリを保存し、Power Query ダイアログを閉じます。ビジュアル クエリが表示されます。 

ビジュアル クエリ エディターのメニューからビューとして保存を選択します。[ビューとして保存] ダイアログが開きます。SQL クエリが使用可能になっていることに注目してください。選択すれば、そのクエリを確認することができます。 

ビュー名に Sales と入力します。 

OK を選択してビューを保存します。 

 

ビューが保存されると、アラートが表示されます。 

[エクスプローラー]パネル (左) で、Views を展開します。新しく作成された Sales ビューがあります。 

 

 

タスク 5: ビジュアル クエリを使用して Product ビューを作成する 

ProductItem、ProductItemGroup、および ProductGroups の各テーブルをマージして、Product ビューを作成しましょう。作業を進めるために、コードを詳細エディターにコピーします。 

レイクハウスのメニュー バーからホーム -> 新規のビジュアル クエリを選択します。新しいビジュアル クエリが開きます。 

[エクスプローラー] セクションから、ProductItem、ProductItemGroup、および ProductGroups の各テーブルを [ビジュアル クエリ] セクションにドラッグします。 

ビジュアル クエリ エディターで、フォーカス モード アイコンを選択して Power Query エディターを開きます。 

 

ProductItem クエリを選択した状態で、リボンからホーム -> クエリのマージ -> 新規としてクエリをマージを選択します。[マージ] ダイアログボックスが開きます。 

 

マージ用の左テーブルで ProductItem を選択します。 

マージ用の右テーブルで ProductItemGroup を選択します。 

両方のテーブルから StockItemID 列を選択します。この列を使用して結合を実行します。 

結合の種類で左外部を選択します。 

[OK] を選択します。新しい Merge クエリが作成されます。 

 

Merge クエリを選択した状態で、リボンからホーム -> 詳細エディターを選択します。[詳細エディター] ダイアログが開きます。 

 

詳細エディターのコードをすべて選択し、削除します。 

次のコードを詳細エディターに貼り付けます。 

let 

   Source = Table.NestedJoin(ProductItem, {"StockItemID"}, ProductItemGroup, {"StockItemID"}, "ProductItemGroup", JoinKind.LeftOuter), 

   #"Expanded ProductItemGroup" = Table.ExpandTableColumn(Source, "ProductItemGroup", {"StockGroupID"}, {"StockGroupID"}), 

   #"Merged queries" = Table.NestedJoin(#"Expanded ProductItemGroup", {"StockGroupID"}, ProductGroups, {"StockGroupID"}, "ProductGroups", JoinKind.LeftOuter), 

   #"Expanded ProductGroups" = Table.ExpandTableColumn(#"Merged queries", "ProductGroups", {"StockGroupName"}, {"StockGroupName"}), 

   #"Choose columns" = Table.SelectColumns(#"Expanded ProductGroups", {"StockItemID", "StockItemName", "SupplierID", "Size", "IsChillerStock", "TaxRate", "UnitPrice", "RecommendedRetailPrice", "TypicalWeightPerUnit", "StockGroupName"}) 

 in 

  #"Choose columns" 

OK を選択して詳細エディターを閉じます。Power Query エディターに戻ります。 

 

左側の [クエリ] パネルで、マージクエリをダブルクリックして、名前を変更します。 

マージクエリを Product という名前に変更します。 

Product クエリを右クリックし、読み込みを有効にするを選択して、クエリが読み込まれるようにします。 

保存を選択してクエリを保存し、Power Query ダイアログを閉じます。ビジュアル クエリが表示されます。 

 

ビジュアル クエリ エディターのメニューからビューとして保存を選択します。[ビューとして保存] ダイアログが開きます。SQL クエリが使用可能になっていることに注目してください。選択すれば、そのクエリを確認することができます。 

ビュー名に Product と入力します。 

OK を選択してビューを保存します。 

 

ビューが保存されると、アラートが表示されます。 

[エクスプローラー]パネル (左) で、Views を展開します。新しく作成された Product ビューがあります。 

 

ADLS Gen2 データソースからデータを変換しました。このラボでは、ショートカットの作成方法を学習し、ビジュアル クエリ ビューを使用してデータを変換するためのさまざまなオプションを確認しました。 

次のラボでは、データフロー (Gen2) の使用方法と別のレイクハウスへのショートカットの作成方法を学習します。 


 
