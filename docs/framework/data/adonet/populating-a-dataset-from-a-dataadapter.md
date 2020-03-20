---
title: Naplnění datové sady z adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: d2d7719c7f6c2cacd6d68ecae226673248bbd680
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149229"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Naplnění datové sady z adaptéru dat
ADO.NET <xref:System.Data.DataSet> je rezidentní reprezentace dat rezidentní v paměti, která poskytuje konzistentní relační programovací model nezávislý na zdroji dat. Představuje `DataSet` úplnou sadu dat, která obsahuje tabulky, omezení a relace mezi tabulkami. Vzhledem `DataSet` k tomu, že `DataSet` je nezávislý na zdroji dat, může obsahovat data místní do aplikace a data z více zdrojů dat. Interakce se stávajícími zdroji `DataAdapter`dat je řízena prostřednictvím .  
  
 Vlastnost `SelectCommand` `DataAdapter` je `Command` objekt, který načítá data ze zdroje dat. `InsertCommand`Vlastnosti `UpdateCommand`, `DeleteCommand` a `DataAdapter` jsou `Command` objekty, které spravují aktualizace dat ve zdroji dat podle `DataSet`změn provedených v datech v . Tyto vlastnosti jsou podrobněji popsány v [aktualizaci zdrojů dat pomocí datových adaptérů](updating-data-sources-with-dataadapters.md).  
  
 Metoda `Fill` `DataAdapter` se používá k naplnění `DataSet` s výsledky `SelectCommand` . `DataAdapter` `Fill`bere jako jeho `DataSet` argumenty a, které `DataTable` mají být naplněny `DataTable` a objekt nebo název, `SelectCommand`který má být vyplněn řádky vrácenými z .  
  
> [!NOTE]
> Použití `DataAdapter` načíst všechny tabulky nějakou dobu trvá, zejména v případě, že existuje mnoho řádků v tabulce. Důvodem je, že přístup k databázi, vyhledání a zpracování dat a potom přenos dat do klienta je časově náročné. Vytažení matné tabulky klientovi také uzamkne všechny řádky na serveru. Chcete-li zlepšit výkon, `WHERE` můžete použít klauzuli výrazně snížit počet řádků vrácených klientovi. Můžete také snížit množství dat vrácených klientovi pouze explicitně `SELECT` výpis požadované sloupce v příkazu. Dalším dobrým řešením je načíst řádky v dávkách (například několik set řádků najednou) a pouze načíst další dávku po dokončení klienta s aktuální dávkou.  
  
 Metoda `Fill` používá `DataReader` objekt implicitně vrátit názvy sloupců a typy, které `DataSet`se používají k vytvoření tabulek v `DataSet`, a data k naplnění řádků tabulek v . Tabulky a sloupce jsou vytvořeny pouze v případě, že ještě neexistují. v `Fill` opačném `DataSet` případě použije existující schéma. Typy sloupců jsou vytvářeny jako typy rozhraní .NET Framework podle tabulek v [části Mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md). Primární klíče nejsou vytvořeny, pokud neexistují `DataAdapter`ve zdroji dat a **.**`MissingSchemaAction` je nastavena na `MissingSchemaAction` **.** `AddWithKey`. Pokud `Fill` zjistí, že pro tabulku existuje primární klíč, přepíše data v souboru `DataSet` s daty ze zdroje dat pro řádky, kde hodnoty sloupce primárního klíče odpovídají hodnotám řádku vráceného ze zdroje dat. Pokud není nalezen žádný primární klíč, data jsou `DataSet`připojena k tabulkám v . `Fill`používá všechna mapování, která mohou `DataSet` existovat při naplnění (viz [DataAdapter DataTable a DataColumn Mappings).](dataadapter-datatable-and-datacolumn-mappings.md)  
  
> [!NOTE]
> Pokud `SelectCommand` vrátí výsledky OUTER JOIN, `DataAdapter` nenastaví `PrimaryKey` hodnotu pro `DataTable`výsledné . Musíte definovat `PrimaryKey` sami, abyste se ujistili, že duplicitní řádky jsou vyřešeny správně. Další informace naleznete [v tématu Definování primárních klíčů](./dataset-datatable-dataview/defining-primary-keys.md).  
  
 Následující příklad kódu vytvoří <xref:System.Data.SqlClient.SqlDataAdapter> instanci, <xref:System.Data.SqlClient.SqlConnection> která používá `Northwind` databázi serveru <xref:System.Data.DataTable> Microsoft `DataSet` SQL Server a naplní seznam zákazníků v a. Příkaz SQL <xref:System.Data.SqlClient.SqlConnection> a argumenty <xref:System.Data.SqlClient.SqlDataAdapter> předané konstruktoru <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> se používají <xref:System.Data.SqlClient.SqlDataAdapter>k vytvoření vlastnosti .  
  
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
> Kód zobrazený v tomto příkladu explicitně neotevře a nezavře . `Connection` Metoda `Fill` implicitně `Connection` otevře, `DataAdapter` že používá, pokud zjistí, že připojení již není otevřen. Pokud `Fill` se připojení otevře, zavře připojení `Fill` také po dokončení. To může zjednodušit kód při zpracování jedné `Fill` operace, `Update`jako je například nebo . Pokud však provádíte více operací, které vyžadují otevřené připojení, můžete zlepšit výkon `Open` aplikace `Connection`explicitním voláním metody , provedením operací `Close` proti `Connection`zdroji dat a voláním metody . Měli byste se pokusit zachovat připojení ke zdroji dat otevřené co nejdříve uvolnit prostředky pro použití jinými klientskými aplikacemi.  
  
## <a name="multiple-result-sets"></a>Více sad výsledků  
 Pokud `DataAdapter` dojde k více sad výsledků, vytvoří `DataSet`více tabulek v . Tabulky mají přírůstkový výchozí název tabulky*N*, počínaje "Tabulka" pro table0. Pokud je název tabulky předán `Fill` metodě jako argument, jsou tabulkám přidělen přírůstkový výchozí název TableName*N*, počínaje názvem TableName pro TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Naplnění datové sady z více datových adaptérů  
 `DataAdapter` S `DataSet`. Každý `DataAdapter` z nich lze použít `DataTable` k vyplnění jednoho nebo více objektů a vyřešit aktualizace zpět do příslušného zdroje dat. `DataRelation`a `Constraint` objekty mohou `DataSet` být přidány místně, což umožňuje propojit data z odlišných zdrojů dat. Může `DataSet` například obsahovat data z databáze serveru Microsoft SQL Server, databáze IBM DB2 vystavené prostřednictvím technologie OLE DB a zdroje dat, který streamuje xml. Jeden nebo `DataAdapter` více objektů může zpracovávat komunikaci s každým zdrojem dat.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu naplní seznam zákazníků `Northwind` z databáze na serveru Microsoft SQL `Northwind` Server a seznam objednávek z databáze uložené v aplikaci Microsoft Access 2000. Vyplněné tabulky souvisejí `DataRelation`s a a seznam zákazníků se pak zobrazí s objednávkami pro tohoto zákazníka. Další informace `DataRelation` o objektech naleznete v [tématech Přidání datových vztahů](./dataset-datatable-dataview/adding-datarelations.md) a [Navigace datových vztahů](./dataset-datatable-dataview/navigating-datarelations.md).  
  
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
  
## <a name="sql-server-decimal-type"></a>Desítkový typ serveru SQL Server  
 Ve výchozím `DataSet` nastavení ukládá data pomocí datových typů rozhraní .NET Framework. Pro většinu aplikací poskytují pohodlné znázornění informací o zdroji dat. Tato reprezentace však může způsobit problém, pokud je datový typ ve zdroji dat desítkový nebo číselný datový typ serveru SQL Server. Datový typ `decimal` rozhraní .NET Framework umožňuje maximálně 28 platných `decimal` číslic, zatímco datový typ serveru SQL Server umožňuje 38 platných číslic. Pokud `SqlDataAdapter` během `Fill` operace určí, že přesnost pole `decimal` serveru SQL Server je větší než 28 `DataTable`znaků, aktuální řádek není přidán do . Místo `FillError` toho dojde k události, která umožňuje určit, zda dojde ke ztrátě přesnosti a odpovídajícím způsobem reagovat. Další informace o `FillError` události naleznete v tématu [Zpracování událostí datového adaptéru](handling-dataadapter-events.md). Chcete-li získat `decimal` hodnotu serveru SQL <xref:System.Data.SqlClient.SqlDataReader> Server, <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> můžete také použít objekt a volat metodu.  
  
 ADO.NET 2.0 zavedla zvýšenou podporu <xref:System.Data.SqlTypes> v . `DataSet` Další informace naleznete [v tématu SqlTypes a DataSet](./sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>Kapitoly OLE DB  
 Hierarchické sady řádků nebo kapitoly (typ `DBTYPE_HCHAPTER`OLE `adChapter`DB , typ ADO) `DataSet`lze použít k vyplnění obsahu . Když <xref:System.Data.OleDb.OleDbDataAdapter> se během operace setká `Fill` se sloupcem s kapitolou, `DataTable` vytvoří se pro sloupec s kapitolami a tato tabulka je vyplněna sloupci a řádky z kapitoly. Tabulka vytvořená pro sloupec s kapitolami je pojmenována pomocí názvu nadřazené tabulky i názvu sloupce s kapitolami ve formuláři*ParentTableNameChapteredColumnName*. Pokud tabulka již existuje `DataSet` v tabulce, která odpovídá názvu sloupce s kapitolou, je aktuální tabulka vyplněna daty kapitoly. Pokud v existující tabulce není žádný sloupec, který by odpovídal sloupci nalezenému v kapitole, je přidán nový sloupec.  
  
 Před tím, `DataSet` než jsou tabulky v tabulce vyplněny daty ve sloupcích s kapitolami, je vytvořen vztah mezi nadřazenou a podřízenou tabulkou hierarchické sady `DataRelation` řádků přidáním celočíselného sloupce do nadřazené i podřízené tabulky, nastavením nadřazeného sloupce na automatický přírůstek a vytvořením přidaných sloupců z obou tabulek. Přidaná relační vazba je pojmenována pomocí názvů nadřazených tabulek a sloupců kapitol ve formuláři*ParentTableNameChapterColumnName.*  
  
 Všimněte si, že související `DataSet`sloupec existuje pouze v . Následné výplně ze zdroje dat mohou způsobit přidání nových řádků do tabulek namísto slučování změn do existujících řádků.  
  
 Všimněte si také, `DataAdapter.Fill` že pokud `DataTable`použijete přetížení, které trvá , bude vyplněna pouze tato tabulka. Do tabulky bude stále přidán sloupec s automatickým přírůstkem celéčíslo, ale nebude vytvořena ani vyplněna žádná podřízená tabulka a nebude vytvořen žádný vztah.  
  
 Následující příklad používá zprostředkovatele MSDataShape ke generování sloupce kapitol objednávek pro každého zákazníka v seznamu zákazníků. A `DataSet` je pak vyplněna daty.  
  
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
  
 Po `Fill` dokončení `DataSet` operace obsahuje dvě tabulky: `Customers` a `CustomersOrders`, kde `CustomersOrders` představuje sloupec s kapitolou. `Orders` Do `Customers` tabulky je přidán další sloupec s názvem `CustomersOrders` a do `CustomersOrders` tabulky je přidán další pojmenovaný sloupec. Sloupec `Orders` v `Customers` tabulce je nastaven na automatický přírůstek. A `DataRelation` `CustomersOrders`, je vytvořen pomocí sloupců, které `Customers` byly přidány do tabulek s jako nadřazené tabulky. V následujících tabulkách jsou uvedeny některé ukázkové výsledky.  
  
### <a name="tablename-customers"></a>Název_tabulky: Zákazníci  
  
|CustomerID|CompanyName|Orders|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y helados|1|  
  
### <a name="tablename-customersorders"></a>Název_tabulky: Objednávky zákazníků  
  
|CustomerID|OrderID|Objednávky zákazníků|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Viz také

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Mapování datového typu v ADO.NET](data-type-mappings-in-ado-net.md)
- [Úpravy dat přes DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Více aktivních sad výsledků (MARS)](./sql/multiple-active-result-sets-mars.md)
- [Přehled ADO.NET](ado-net-overview.md)
