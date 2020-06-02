---
title: Naplnění datové sady z adaptéru dat
description: Naučte se naplnit datovou sadu z DataAdapter v ADO.NET, která poskytuje konzistentní relační programovací model nezávislý na zdroji dat.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: 3d4da840e1d51ec6f309915787caa8891db3eb59
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286660"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Naplnění datové sady z adaptéru dat
ADO.NET <xref:System.Data.DataSet> je reprezentace dat rezidenta v paměti, která poskytuje konzistentní relační programovací model nezávislý na zdroji dat. `DataSet`Představuje kompletní sadu dat, která zahrnuje tabulky, omezení a vztahy mezi tabulkami. Vzhledem k tomu `DataSet` , že je nezávislý na zdroji dat, `DataSet` může do aplikace zahrnout data místní a data z více zdrojů dat. Interakce s existujícími zdroji dat je řízena prostřednictvím `DataAdapter` .  
  
 `SelectCommand`Vlastnost `DataAdapter` je `Command` objekt, který načítá data ze zdroje dat. `InsertCommand`Vlastnosti, `UpdateCommand` a `DeleteCommand` `DataAdapter` jsou `Command` objekty, které spravují aktualizace dat ve zdroji dat v souladu s úpravami provedenými v datech v `DataSet` . Tyto vlastnosti jsou podrobněji popsány v části [aktualizace zdrojů dat pomocí datových adaptérů](updating-data-sources-with-dataadapters.md).  
  
 `Fill`Metoda `DataAdapter` je použita k naplnění výsledků z `DataSet` `SelectCommand` `DataAdapter` . `Fill`přijímá jako argumenty a `DataSet` k naplnění, `DataTable` objekt nebo název, který `DataTable` má být vyplněn řádky vrácenými z `SelectCommand` .  
  
> [!NOTE]
> Použití `DataAdapter` pro načtení všech tabulek vybere čas, zejména v případě, že je v tabulce mnoho řádků. Důvodem je to, že přístup k databázi, vyhledání a zpracování dat a následné přenos dat do klienta je časově náročný. Když se všechny tabulky nastahují do klienta, zamkne se i všechny řádky na serveru. Chcete-li zvýšit výkon, můžete použít `WHERE` klauzuli k výraznému snížení počtu řádků vrácených klientovi. Množství dat vrácených klientovi můžete také omezit pouze explicitně uvedením požadovaných sloupců v `SELECT` příkazu. Dalším dobrým řešením je načíst řádky v dávkách (například několik stovky řádků najednou) a načíst další dávku pouze v případě, že je klient dokončen s aktuální dávkou.  
  
 `Fill`Metoda používá `DataReader` objekt implicitně k vrácení názvů sloupců a typů, které se používají k vytvoření tabulky v nástroji `DataSet` , a data k naplnění řádků tabulek v `DataSet` . Tabulky a sloupce jsou vytvořeny pouze v případě, že ještě neexistují; v opačném případě `Fill` použije existující `DataSet` schéma. Typy sloupců jsou vytvořeny jako .NET Framework typy podle tabulek v [mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md). Primární klíče se nevytvoří, pokud ve zdroji dat neexistují `DataAdapter` **.**`MissingSchemaAction` je nastaven na `MissingSchemaAction` **.** `AddWithKey` . Pokud aplikace `Fill` zjistí, že primární klíč pro tabulku existuje, přepíše data v `DataSet` datech ze zdroje dat pro řádky, ve kterých se hodnoty sloupce primárního klíče shodují s hodnotami vrácenými ze zdroje dat. Pokud se nenajde žádný primární klíč, data se připojí k tabulkám v `DataSet` . `Fill`používá všechna mapování, která mohou existovat při naplňování `DataSet` (viz [DataAdapter DataTable a DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
> Vrátí-li `SelectCommand` funkce výsledky vnějšího spojení, `DataAdapter` nenastaví `PrimaryKey` hodnotu pro výsledný výsledek `DataTable` . Abyste měli `PrimaryKey` jistotu, že se duplicitní řádky vyřeší správně, musíte definovat sami sebe. Další informace najdete v tématu [Definování primárních klíčů](./dataset-datatable-dataview/defining-primary-keys.md).  
  
 Následující příklad kódu vytvoří instanci <xref:System.Data.SqlClient.SqlDataAdapter> , která používá <xref:System.Data.SqlClient.SqlConnection> k Microsoft SQL Server `Northwind` databázi a naplní <xref:System.Data.DataTable> `DataSet` ji seznamem zákazníků. Příkaz jazyka SQL a <xref:System.Data.SqlClient.SqlConnection> argumenty předané <xref:System.Data.SqlClient.SqlDataAdapter> konstruktoru jsou použity k vytvoření <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> vlastnosti <xref:System.Data.SqlClient.SqlDataAdapter> .  
  
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
> Kód zobrazený v tomto příkladu explicitně neotevře a neuzavře `Connection` . `Fill`Metoda implicitně otevře rozhraní `Connection` , které používá, `DataAdapter` Pokud zjistí, že připojení již není otevřeno. Pokud `Fill` se připojení otevřelo, ukončí se i po `Fill` dokončení připojení. To může zjednodušit váš kód při práci s jednou operací, jako je například `Fill` nebo `Update` . Pokud však provádíte více operací, které vyžadují otevřené připojení, můžete zvýšit výkon aplikace explicitním voláním `Open` metody `Connection` , provedení operací proti zdroji dat a následným voláním `Close` metody `Connection` . Měli byste se pokusit o udržování připojení ke zdroji dat co nejdříve, pokud chcete uvolnit prostředky pro použití jinými klientskými aplikacemi.  
  
## <a name="multiple-result-sets"></a>Více sad výsledků  
 Pokud `DataAdapter` dojde k více výsledkům sady výsledků, vytvoří se několik tabulek v `DataSet` . Tabulkám se předává přírůstkový výchozí název tabulky*N*, od "Table" pro TABLE0. Pokud je název tabulky předán jako argument pro `Fill` metodu, tabulky jsou předány přírůstkovým výchozím názvem TableName*N*, počínaje hodnotou "TableName" pro TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Naplnění datové sady z více datových adaptérů  
 Libovolný počet `DataAdapter` objektů lze použít s `DataSet` . Každý `DataAdapter` lze použít k vyplnění jednoho nebo více `DataTable` objektů a vyřešení aktualizací zpět na relevantní zdroj dat. `DataRelation`objekty a je `Constraint` možné přidávat `DataSet` místně, což umožňuje propojit data z odlišných zdrojů dat. `DataSet`Může například obsahovat data z databáze Microsoft SQL Server, databázi IBM DB2 zveřejněnou prostřednictvím OLE DB a zdroj dat, který streamuje XML. Jeden nebo více `DataAdapter` objektů může zpracovávat komunikaci s každým zdrojem dat.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu naplní seznam zákazníků z `Northwind` databáze na Microsoft SQL Server a seznam objednávek z `Northwind` databáze uložené v aplikaci Microsoft Access 2000. Vyplněné tabulky se vztahují k `DataRelation` a seznam zákazníků se pak zobrazí s objednávkami daného zákazníka. Další informace o `DataRelation` objektech naleznete v tématu [Přidání datových vztahů](./dataset-datatable-dataview/adding-datarelations.md) a navigace v datových [vztazích](./dataset-datatable-dataview/navigating-datarelations.md).  
  
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
  
## <a name="sql-server-decimal-type"></a>SQL Server Typ Decimal  
 Ve výchozím nastavení `DataSet` ukládá data pomocí .NET Framework datových typů. Pro většinu aplikací poskytují tyto informace užitečné znázornění informací o zdroji dat. Tato reprezentace ale může způsobit potíže, pokud je datový typ ve zdroji dat SQL Server desítkový nebo číselný datový typ. `decimal`Datový typ .NET Framework umožňuje maximálně 28 platných číslic, zatímco `decimal` datový typ SQL Server umožňuje 38 platných číslic. Pokud v rámci `SqlDataAdapter` operace určíte `Fill` , že přesnost SQL Serverho `decimal` pole je větší než 28 znaků, aktuální řádek není přidán do `DataTable` . Místo toho `FillError` dojde k události, která umožňuje určit, zda dojde ke ztrátě přesnosti, a odpovídajícím způsobem reagovat. Další informace o `FillError` události naleznete v tématu [zpracování událostí DataAdapter](handling-dataadapter-events.md). Chcete-li získat SQL Server `decimal` hodnotu, můžete také použít <xref:System.Data.SqlClient.SqlDataReader> objekt a volat <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> metodu.  
  
 ADO.NET 2,0 představil rozšířenou podporu pro <xref:System.Data.SqlTypes> v nástroji `DataSet` . Další informace naleznete v tématu [SqlTypes a DataSet](./sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB kapitoly  
 Hierarchické sady řádků nebo kapitoly (typ OLE DB `DBTYPE_HCHAPTER` , typ ADO `adChapter` ) lze použít k vyplnění obsahu `DataSet` . Když <xref:System.Data.OleDb.OleDbDataAdapter> dojde k vyplňování sloupce v kapitole v rámci `Fill` operace, vytvoří `DataTable` se pro sloupec kapitoly a tato tabulka se vyplní sloupci a řádky z této kapitoly. Tabulka vytvořená pro sloupec s názvem kapitoly je pojmenována pomocí názvu nadřazené tabulky a názvu sloupce kapitoly ve formátu "*ParentTableNameChapteredColumnName*". Pokud tabulka již existuje v `DataSet` , která se shoduje s názvem sloupce v kapitole, je aktuální tabulka doplněna daty kapitoly. Pokud v existující tabulce není žádný sloupec, který by odpovídal sloupci nalezenému v této kapitole, je přidán nový sloupec.  
  
 Předtím, než jsou tabulky v poli `DataSet` vyplněny daty ze sloupců v poli kapitoly, je vytvořena relace mezi nadřazenými a podřízenými tabulkami hierarchické sady řádků přidáním celého čísla do nadřazené a podřízené tabulky, nastavením nadřazeného sloupce na Automatický přírůstek a vytvořením `DataRelation` pomocí přidaných sloupců z obou tabulek. Přidaný vztah je pojmenován pomocí nadřazené tabulky a názvů sloupců kapitoly ve formátu "*ParentTableNameChapterColumnName*".  
  
 Všimněte si, že související sloupec existuje pouze v `DataSet` . Další výplně ze zdroje dat mohou způsobit, že se do tabulek přidají nové řádky místo sloučení změn do stávajících řádků.  
  
 Všimněte si také, že pokud použijete `DataAdapter.Fill` přetížení, které používá `DataTable` , bude vyplněno pouze tato tabulka. Do tabulky bude stále přidán sloupec s automatickým přírůstkovým celým číslem, ale nebude vytvořena ani žádná podřízená tabulka a nebude vytvořena žádná relace.  
  
 Následující příklad používá poskytovatele MSDataShape k vygenerování sloupce kapitoly objednávek pro každého zákazníka v seznamu zákazníků. A `DataSet` pak se vyplní daty.  
  
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
  
 Po `Fill` dokončení operace `DataSet` obsahuje dvě tabulky: `Customers` a `CustomersOrders` , kde `CustomersOrders` představuje sloupec v kapitolě. `Orders`Do tabulky se přidá další sloupec s názvem `Customers` a `CustomersOrders` do tabulky se přidá další sloupec s názvem `CustomersOrders` . `Orders`Sloupec v `Customers` tabulce je nastaven na hodnotu Automatický přírůstek. A `DataRelation` , `CustomersOrders` , je vytvořen pomocí sloupců, které byly přidány do tabulek s `Customers` jako nadřazenou tabulkou. V následujících tabulkách jsou uvedeny některé příklady výsledků.  
  
### <a name="tablename-customers"></a>TableName: zákazníci  
  
|CustomerID|CompanyName|Orders|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y Helados|1|  
  
### <a name="tablename-customersorders"></a>TableName: CustomersOrders  
  
|CustomerID|OrderID|CustomersOrders|  
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
