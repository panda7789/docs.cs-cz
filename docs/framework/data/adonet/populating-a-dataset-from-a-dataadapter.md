---
title: "Naplnění datové sady z modul DataAdapter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c0991398a28e491d381d10dea8a14ed463c67c89
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Naplnění datové sady z modul DataAdapter
[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataSet> Je rezidentní reprezentace data, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat. `DataSet` Představuje kompletní sadu dat, který obsahuje tabulky, omezení a relace mezi tabulkami. Protože `DataSet` je nezávislý na zdroji dat, `DataSet` může obsahovat data místní aplikace a data z více zdrojů dat. Interakce s existujícími zdroji dat jsou řízeny prostřednictvím `DataAdapter`.  
  
 `SelectCommand` Vlastnost `DataAdapter` je `Command` objekt, který načte data z datového zdroje. `InsertCommand`, `UpdateCommand`, A `DeleteCommand` vlastnosti `DataAdapter` jsou `Command` objekty, které spravují aktualizace dat ve zdroji dat podle změny provedené v datech v `DataSet`. Tyto vlastnosti jsou popsané v podrobněji [aktualizace zdroje dat s DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 `Fill` Metodu `DataAdapter` se používá k naplnění `DataSet` s výsledky `SelectCommand` z `DataAdapter`. `Fill`vezme jako jeho argumenty `DataSet` vyplnit a `DataTable` objekt nebo název `DataTable` pro vyplnění pomocí řádků vrácených `SelectCommand`.  
  
> [!NOTE]
>  Pomocí `DataAdapter` načíst všechny tabulky trvá určitou dobu, hlavně v případě, že je velký počet řádků v tabulce. Důvodem je, že přístup k databázi, vyhledání a zpracování dat, a potom přenos dat do klienta je časově náročná. Všechny tabulky stahování do klienta zamkne taky všechny řádky na serveru. Chcete-li zvýšit výkon, můžete použít `WHERE` klauzule výrazně omezit počet řádků, je vrácen do klienta. Můžete také snížit množství dat vrácen do klienta tak, že pouze explicitně uvedete požadované sloupce v `SELECT` příkaz. Jiné dobrým řešením je načíst řádky v dávkách (například několik set řádky v čase) a další dávku načíst pouze po dokončení aktuální dávkou klienta.  
  
 `Fill` Metoda používá `DataReader` objekt implicitně vrátí názvy sloupců a typy, které se používají k vytváření tabulek v `DataSet`a data k naplnění řádky z tabulky v `DataSet`. Tabulky a sloupce jsou vytvářeny, pouze pokud už neexistují; v opačném případě `Fill` používá existující `DataSet` schématu. Typy sloupců jsou vytvořené jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typů podle tabulky v [mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md). Primární klíče, které nejsou vytvořeny, pokud existují ve zdroji dat a `DataAdapter` **.**`MissingSchemaAction` je nastavena na `MissingSchemaAction` **.** `AddWithKey`. Pokud `Fill` zjistí, že primární klíč pro tabulku existuje, přepíše data `DataSet` s daty ze zdroje dat pro řádky, kde hodnoty sloupec primárního klíče shodovat s hodnotami řádku vrátí ze zdroje dat. Pokud se nenajde žádný primární klíč, připojí se data k tabulky v `DataSet`. `Fill`používá všech mapování, která mohou existovat při naplňování `DataSet` (najdete v části [DataAdapter DataTable a mapování DataColumn](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
>  Pokud `SelectCommand` vrátí výsledky z vnějšího spojení, `DataAdapter` nenastaví `PrimaryKey` výsledná hodnota `DataTable`. Je nutné definovat `PrimaryKey` sami, abyste měli jistotu, že jsou správně přeložit duplicitní řádky. Další informace najdete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Následující příklad kódu vytvoří instance <xref:System.Data.SqlClient.SqlDataAdapter> používající <xref:System.Data.SqlClient.SqlConnection> Microsoft SQL Server `Northwind` databáze a naplní <xref:System.Data.DataTable> v `DataSet` se do seznamu zákazníků. Příkaz jazyka SQL a <xref:System.Data.SqlClient.SqlConnection> předáno argumentů <xref:System.Data.SqlClient.SqlDataAdapter> konstruktor se používají k vytvoření <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> vlastnost <xref:System.Data.SqlClient.SqlDataAdapter>.  
  
## <a name="example"></a>Příklad  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim queryString As String = _  
  "SELECT CustomerID, CompanyName FROM dbo.Customers"  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  queryString, connection)  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
string queryString =   
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  Kód zobrazí v tomto příkladu se neotevře explicitně a zavřete `Connection`. `Fill` Metoda implicitně otevře `Connection` , `DataAdapter` používá, jestliže zjistí, že připojení není již otevřený. Pokud `Fill` otevřít připojení, také uzavře připojení při `Fill` po dokončení. Když budete pracovat s jedinou operací, jako to může zjednodušit kódu `Fill` nebo `Update`. Ale pokud provádíte více operací, které vyžadují otevřené připojení, můžete zlepšit výkon aplikace explicitně volání `Open` metodu `Connection`, provádění operací na zdroji dat a potom volání `Close` metodu `Connection`. Doporučujeme nechat připojení ke zdroji dat otevřené jako stručně kvůli uvolnění prostředků pro použití v jiných klientských aplikacích.  
  
## <a name="multiple-result-sets"></a>Více sad výsledků dotazu  
 Pokud `DataAdapter` komunikaci sady více výsledků, dojde k několika tabulkám ve `DataSet`. V tabulkách jsou uvedeny přírůstkové výchozí název tabulky*N*, od verze "Tabulka" pro Table0. Pokud je název tabulky předat jako argument k `Fill` metoda, v tabulkách jsou uvedeny přírůstkové výchozí název TableName*N*, od verze "TableName" pro TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Naplnění datové sady z více DataAdapters  
 Libovolný počet `DataAdapter` objekty lze použít s `DataSet`. Každý `DataAdapter` lze použít k vyplnění jeden nebo více `DataTable` objekty a vyřešte aktualizace zpět do zdroje dat relevantní. `DataRelation`a `Constraint` objekty mohou být přidány do `DataSet` místně, což umožňuje související data ze zdrojů dat v odlišných typů. Například `DataSet` může obsahovat data z databáze Microsoft SQL Server, k databázi IBM DB2 vystavenou přes OLE DB a zdroj dat, který datové proudy XML. Jeden nebo více `DataAdapter` objekty může zpracovávat komunikaci pro každý zdroj dat.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu naplní seznam zákazníků z `Northwind` databáze na serveru Microsoft SQL Server a seznam objednávky z `Northwind` databáze uložené v aplikaci Microsoft Access 2000. Vyplnění tabulky souvisejí s `DataRelation`, a pak je do seznamu zákazníků se zobrazují s objednávky tohoto zákazníka. Další informace o `DataRelation` objekty, najdete v části [přidání DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) a [navigace DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).  
  
```vb  
' Assumes that customerConnection is a valid SqlConnection object.  
' Assumes that orderConnection is a valid OleDbConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", customerConnection)  
  
Dim ordAdapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SELECT * FROM Orders", orderConnection)  
  
Dim customerOrders As DataSet = New DataSet()  
custAdapter.Fill(customerOrders, "Customers")  
ordAdapter.Fill(customerOrders, "Orders")  
  
Dim relation As DataRelation = _  
  customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustomerID"), _   
  customerOrders.Tables("Orders").Columns("CustomerID"))  
  
Dim pRow, cRow As DataRow  
For Each pRow In customerOrders.Tables("Customers").Rows  
  Console.WriteLine(pRow("CustomerID").ToString())  
  
  For Each cRow In pRow.GetChildRows(relation)  
    Console.WriteLine(vbTab & cRow("OrderID").ToString())  
  Next  
Next  
```  
  
```csharp  
// Assumes that customerConnection is a valid SqlConnection object.  
// Assumes that orderConnection is a valid OleDbConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", customerConnection);  
OleDbDataAdapter ordAdapter = new OleDbDataAdapter(  
  "SELECT * FROM Orders", orderConnection);  
  
DataSet customerOrders = new DataSet();  
  
custAdapter.Fill(customerOrders, "Customers");  
ordAdapter.Fill(customerOrders, "Orders");  
  
DataRelation relation = customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustomerID"],  
  customerOrders.Tables["Orders"].Columns["CustomerID"]);  
  
foreach (DataRow pRow in customerOrders.Tables["Customers"].Rows)  
{  
  Console.WriteLine(pRow["CustomerID"]);  
   foreach (DataRow cRow in pRow.GetChildRows(relation))  
    Console.WriteLine("\t" + cRow["OrderID"]);  
}  
```  
  
## <a name="sql-server-decimal-type"></a>SQL Server Decimal Type  
 Ve výchozím nastavení `DataSet` ukládá data pomocí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] datové typy. Pro většinu aplikací tyto poskytují pohodlný reprezentace informace o zdroji dat. Tento zápis však může způsobit problém, když je typ dat ve zdroji dat desítkový nebo číselný datový typ SQL serveru. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` Datový typ povoluje maximálně 28 platných číslic, zatímco SQL Server `decimal` datový typ umožňuje 38 platných číslic. Pokud `SqlDataAdapter` určuje během `Fill` operace, přesnost systému SQL Server `decimal` pole je větší než 28 znaků, že aktuálnímu řádku není přidáno do `DataTable`. Místo toho `FillError` dojde k události, které umožňuje určit, zda bude ztrátu přesnosti dojít a reagují odpovídajícím způsobem. Další informace o `FillError` událostí, najdete v části [zpracování události DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md). Získat systému SQL Server `decimal` hodnotu, můžete použít také <xref:System.Data.SqlClient.SqlDataReader> objekt a volání <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> metoda.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]2.0 zavedená rozšířenou podporu <xref:System.Data.SqlTypes> v `DataSet`. Další informace najdete v tématu [SqlTypes a datovou sadu](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB kapitolám  
 Hierarchická sady řádků či kapitolám (typ OLE DB `DBTYPE_HCHAPTER`, typ ADO `adChapter`) lze použít k vyplnění obsah `DataSet`. Když <xref:System.Data.OleDb.OleDbDataAdapter> zaznamená sloupec nepoužívaly kapitoly během `Fill` operace, `DataTable` se vytvoří nepoužívaly kapitoly ve sloupci a tato tabulka je plná sloupců a řádků z kapitoly. V tabulce vytvořené pro nepoužívaly kapitoly sloupec nazýval pomocí názvu nadřazené tabulky a název sloupce nepoužívaly kapitoly ve tvaru "*ParentTableNameChapteredColumnName*". Pokud tabulka již existuje v `DataSet` odpovídající názvu nepoužívaly kapitoly sloupce, v aktuální tabulce, naplní se kapitoly data. Pokud je existující tabulky, který odpovídá sloupci najít v kapitole žádný sloupec, nový sloupec přidán.  
  
 Před tabulky v `DataSet` jsou vyplněny s daty ve sloupcích nepoužívaly kapitoly, vytvoření vztahu mezi nadřazenými a podřízenými tabulky hierarchické řádků přidáním sloupec celé číslo do nadřazené a podřízené tabulky, nastavení nadřazeného sloupce automatickým krokem a vytváření `DataRelation` použití přidaných sloupců z obou tabulek. Přidání vztah jmenuje pomocí nadřazené názvy sloupců tabulky a kapitoly ve tvaru "*ParentTableNameChapterColumnName*".  
  
 Všimněte si, že v pouze existuje sloupec v relaci `DataSet`. Následné výplněmi ze zdroje dat může způsobit nové řádky, které chcete přidat do tabulky místo změny slučování do existujících řádků.  
  
 Všimněte si také, že pokud použijete `DataAdapter.Fill` přetížení, které přijímá `DataTable`, bude vyplněno pouze tuto tabulku. Sloupec automaticky rostoucí celé číslo se stále zařadí do tabulky, ale žádné podřízené tabulky se vytvoří nebo vyplněna a vytvoří se žádný vztah.  
  
 Následující příklad používá zprostředkovatele MSDataShape ke generování objednávek každému zákazníkovi neočekávaný sloupec kapitoly v seznamu zákazníků. A `DataSet` pak, naplní se data.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=northwind")  
  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
  
Dim customers As DataSet = New DataSet()  
  
adapter.Fill(customers, "Customers")  
End Using  
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection("Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=(local);Integrated Security=SSPI;Initial Catalog=northwind"))  
{  
OleDbDataAdapter adapter = new OleDbDataAdapter("SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
}  
```  
  
 Když `Fill` bylo dokončeno, `DataSet` obsahuje dvě tabulky: `Customers` a `CustomersOrders`, kde `CustomersOrders` představuje nepoužívaly kapitoly sloupec. Sloupec s názvem `Orders` se přidá do `Customers` tabulky a další sloupec s názvem `CustomersOrders` se přidá do `CustomersOrders` tabulky. `Orders` Sloupec v `Customers` tabulky je nastavena na automatickým krokem. A `DataRelation`, `CustomersOrders`, se vytvoří pomocí sloupců, které byly přidány do tabulky s `Customers` jako v nadřazené tabulce. Následující tabulky uvádí některé ukázkové výsledky.  
  
### <a name="tablename-customers"></a>Název tabulky: zákazníků  
  
|CustomerID|CompanyName|Objednávky|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y helados|1|  
  
### <a name="tablename-customersorders"></a>Název tabulky: CustomersOrders  
  
|CustomerID|OrderID|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [Úpravy dat přes DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [Více aktivních sad výsledků (MARS)](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
