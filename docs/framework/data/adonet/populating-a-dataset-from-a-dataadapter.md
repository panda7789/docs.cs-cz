---
title: Naplnění datové sady z adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: fecc212b21fee585444db35d832894719640fd79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783212"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Naplnění datové sady z adaptéru dat
ADO.NET <xref:System.Data.DataSet> je reprezentace dat rezidenta v paměti, která poskytuje konzistentní relační programovací model nezávislý na zdroji dat. `DataSet` Představuje kompletní sadu dat, která zahrnuje tabulky, omezení a vztahy mezi tabulkami. Vzhledem k tomu, že `DataSet` jenezávislýnazdrojidat,můžedoaplikacezahrnoutdatamístníadatazvícezdrojůdat.`DataSet` Interakce s existujícími zdroji dat je řízena `DataAdapter`prostřednictvím.  
  
 `SelectCommand` Vlastnost jeobjekt`Command` , který načítá data ze zdroje dat. `DataAdapter` `InsertCommand`Vlastnosti ,`UpdateCommand`a jsou`DeleteCommand` objekty,`DataSet`které spravují aktualizace dat ve zdroji dat v souladu s úpravami provedenými v datech v. `Command` `DataAdapter` Tyto vlastnosti jsou podrobněji popsány v části [aktualizace zdrojů dat pomocí datových adaptérů](updating-data-sources-with-dataadapters.md).  
  
 `Fill` Metoda `SelectCommand` jepoužita`DataSet` k naplnění výsledků`DataAdapter`z. `DataAdapter` `Fill`přijímá jako argumenty `DataSet` a k naplnění, `DataTable` objekt `DataTable` nebo název, který má `SelectCommand`být vyplněn řádky vrácenými z.  
  
> [!NOTE]
> `DataAdapter` Použití pro načtení všech tabulek vybere čas, zejména v případě, že je v tabulce mnoho řádků. Důvodem je to, že přístup k databázi, vyhledání a zpracování dat a následné přenos dat do klienta je časově náročný. Když se všechny tabulky nastahují do klienta, zamkne se i všechny řádky na serveru. Chcete-li zvýšit výkon, můžete použít `WHERE` klauzuli k výraznému snížení počtu řádků vrácených klientovi. Množství dat vrácených klientovi můžete také omezit pouze explicitně uvedením požadovaných sloupců v `SELECT` příkazu. Dalším dobrým řešením je načíst řádky v dávkách (například několik stovky řádků najednou) a načíst další dávku pouze v případě, že je klient dokončen s aktuální dávkou.  
  
 Metoda používá objekt implicitně k vrácení názvů sloupců a typů, které se používají k `DataSet`vytvoření tabulky v nástroji, a data k `DataSet`naplnění řádků tabulek v. `DataReader` `Fill` Tabulky a sloupce jsou vytvořeny pouze v případě, že ještě neexistují; v `Fill` opačném případě `DataSet` použije existující schéma. Typy sloupců jsou vytvořeny jako .NET Framework typy podle tabulek v [mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md). Primární klíče se nevytvoří, pokud ve zdroji `DataAdapter`dat neexistují **.** `MissingSchemaAction` je nastaven na `MissingSchemaAction` **.** `AddWithKey`. Pokud `Fill` aplikace zjistí, že primární klíč pro tabulku existuje, přepíše data `DataSet` v datech ze zdroje dat pro řádky, ve kterých se hodnoty sloupce primárního klíče shodují s hodnotami vrácenými ze zdroje dat. Pokud se nenajde žádný primární klíč, data se připojí k tabulkám v `DataSet`. `Fill`používá všechna mapování, která mohou existovat při naplňování `DataSet` (viz [DataAdapter DataTable a DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
> Vrátí-li funkce výsledky vnějšího spojení `DataAdapter` , nenastaví `PrimaryKey` hodnotu pro výsledný `DataTable`výsledek. `SelectCommand` Abyste měli jistotu, `PrimaryKey` že se duplicitní řádky vyřeší správně, musíte definovat sami sebe. Další informace najdete v tématu [Definování primárních klíčů](./dataset-datatable-dataview/defining-primary-keys.md).  
  
 Následující <xref:System.Data.SqlClient.SqlDataAdapter> příklad kódu vytvoří instanci, která <xref:System.Data.SqlClient.SqlConnection> používá k Microsoft SQL Server `Northwind` databázi a naplní <xref:System.Data.DataTable> `DataSet` ji seznamem zákazníků. Příkaz jazyka SQL a <xref:System.Data.SqlClient.SqlConnection> argumenty předané <xref:System.Data.SqlClient.SqlDataAdapter> konstruktoru <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> jsou použity k <xref:System.Data.SqlClient.SqlDataAdapter>vytvoření vlastnosti.  
  
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
> Kód zobrazený v tomto příkladu explicitně neotevře a neuzavře `Connection`. Metoda implicitně otevře rozhraní `Connection` , které používá `DataAdapter` , pokud zjistí, že připojení již není otevřeno. `Fill` Pokud `Fill` se připojení otevřelo, ukončí se i po `Fill` dokončení připojení. To může zjednodušit váš kód při práci s jednou operací, jako je `Fill` například `Update`nebo. Pokud však provádíte více operací, které vyžadují otevřené připojení, můžete zvýšit výkon aplikace explicitním voláním `Open` metody `Connection`, provedení operací proti zdroji dat a pak zavolejte `Close` metodu `Connection`. Měli byste se pokusit o udržování připojení ke zdroji dat co nejdříve, pokud chcete uvolnit prostředky pro použití jinými klientskými aplikacemi.  
  
## <a name="multiple-result-sets"></a>Více sad výsledků  
 Pokud dojde `DataAdapter` k více výsledkům sady výsledků, vytvoří se několik tabulek `DataSet`v. Tabulkám se předává přírůstkový výchozí název tabulky*N*, od "Table" pro TABLE0. Pokud je název tabulky předán jako argument pro `Fill` metodu, tabulky jsou předány přírůstkovým výchozím názvem TableName*N*, počínaje hodnotou "TableName" pro TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Naplnění datové sady z více datových adaptérů  
 Libovolný počet `DataAdapter` objektů lze použít `DataSet`s. Každý `DataAdapter` lze použít k vyplnění jednoho nebo více `DataTable` objektů a vyřešení aktualizací zpět na relevantní zdroj dat. `DataRelation`objekty `Constraint` a je možné přidávat `DataSet` místně, což umožňuje propojit data z odlišných zdrojů dat. `DataSet` Může například obsahovat data z databáze Microsoft SQL Server, databázi IBM DB2 zveřejněnou prostřednictvím OLE DB a zdroj dat, který streamuje XML. Jeden nebo více `DataAdapter` objektů může zpracovávat komunikaci s každým zdrojem dat.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu naplní seznam zákazníků z `Northwind` databáze na Microsoft SQL Server a seznam objednávek `Northwind` z databáze uložené v aplikaci Microsoft Access 2000. Vyplněné tabulky se vztahují `DataRelation`k a seznam zákazníků se pak zobrazí s objednávkami daného zákazníka. Další informace o `DataRelation` objektech naleznete v tématu [Přidání datových vztahů](./dataset-datatable-dataview/adding-datarelations.md) a navigace v datových [vztazích](./dataset-datatable-dataview/navigating-datarelations.md).  
  
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
 Ve výchozím nastavení `DataSet` ukládá data pomocí .NET Framework datových typů. Pro většinu aplikací poskytují tyto informace užitečné znázornění informací o zdroji dat. Tato reprezentace ale může způsobit potíže, pokud je datový typ ve zdroji dat SQL Server desítkový nebo číselný datový typ. Datový typ `decimal` .NET Framework umožňuje maximálně 28 platných číslic, zatímco datový typ SQL Server `decimal` umožňuje 38 platných číslic. Pokud v `SqlDataAdapter` `Fill` rámci operace určíte, že přesnost SQL Serverho `decimal` pole je větší než 28 znaků, aktuální řádek není přidán do `DataTable`. Místo toho dojde k události,kteráumožňujeurčit,zdadojdekeztrátěpřesnosti,aodpovídajícímzpůsobemreagovat.`FillError` Další informace o `FillError` události naleznete v tématu [zpracování událostí DataAdapter](handling-dataadapter-events.md). Chcete-li získat `decimal` SQL Server hodnotu, můžete také <xref:System.Data.SqlClient.SqlDataReader> použít objekt a volat <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> metodu.  
  
 ADO.NET 2,0 představil rozšířenou podporu <xref:System.Data.SqlTypes> pro `DataSet`v nástroji. Další informace naleznete v tématu [SqlTypes a DataSet](./sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB kapitoly  
 Hierarchické sady řádků nebo kapitoly (typ OLE DB `DBTYPE_HCHAPTER`, typ `adChapter`ADO) lze použít k `DataSet`vyplnění obsahu. Když dojde <xref:System.Data.OleDb.OleDbDataAdapter> k vyplňování sloupce `Fill` v kapitole v rámci operace, vytvoří `DataTable` se pro sloupec kapitoly a tato tabulka se vyplní sloupci a řádky z této kapitoly. Tabulka vytvořená pro sloupec s názvem kapitoly je pojmenována pomocí názvu nadřazené tabulky a názvu sloupce kapitoly ve formátu "*ParentTableNameChapteredColumnName*". Pokud tabulka již existuje v `DataSet` , která se shoduje s názvem sloupce v kapitole, je aktuální tabulka doplněna daty kapitoly. Pokud v existující tabulce není žádný sloupec, který by odpovídal sloupci nalezenému v této kapitole, je přidán nový sloupec.  
  
 Před tím, než jsou `DataSet` tabulky v poli vyplněny daty ve sloupcích v jazyce, je vytvořena relace mezi nadřazenými a podřízenými tabulkami hierarchické sady řádků přidáním celočíselného sloupce do nadřazené i podřízené tabulky a nastavením nadřazeného sloupce. Automatický přírůstek a vytvoření `DataRelation` pomocí přidaných sloupců z obou tabulek. Přidaný vztah je pojmenován pomocí nadřazené tabulky a názvů sloupců kapitoly ve formátu "*ParentTableNameChapterColumnName*".  
  
 Všimněte si, že související sloupec existuje pouze v `DataSet`. Další výplně ze zdroje dat mohou způsobit, že se do tabulek přidají nové řádky místo sloučení změn do stávajících řádků.  
  
 Všimněte si také, že pokud použijete `DataAdapter.Fill` přetížení, které `DataTable`používá, bude vyplněno pouze tato tabulka. Do tabulky bude stále přidán sloupec s automatickým přírůstkovým celým číslem, ale nebude vytvořena ani žádná podřízená tabulka a nebude vytvořena žádná relace.  
  
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
  
 `Customers` `CustomersOrders`Po dokončení `Fill` `DataSet` operace obsahuje dvě tabulky: a, kde `CustomersOrders` představuje sloupec v kapitolě. Do tabulky se přidá `Orders` další sloupec s názvem a do `CustomersOrders` tabulky se přidá další sloupec `CustomersOrders`snázvem. `Customers` `Orders` Sloupec`Customers` v tabulce je nastaven na hodnotu Automatický přírůstek. A `DataRelation` `Customers` , `CustomersOrders`, je vytvořen pomocí sloupců, které byly přidány do tabulek s jako nadřazenou tabulkou. V následujících tabulkách jsou uvedeny některé příklady výsledků.  
  
### <a name="tablename-customers"></a>Tabulky Klientů  
  
|ID|CompanyName|Fakt|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y Helados|1|  
  
### <a name="tablename-customersorders"></a>Tabulky CustomersOrders  
  
|ID|Seskup|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Viz také:

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Mapování datového typu v ADO.NET](data-type-mappings-in-ado-net.md)
- [Úpravy dat přes DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Více aktivních sad výsledků (MARS)](./sql/multiple-active-result-sets-mars.md)
- [Přehled ADO.NET](ado-net-overview.md)
