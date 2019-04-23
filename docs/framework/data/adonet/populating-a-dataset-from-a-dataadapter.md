---
title: Naplnění datové sady z adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: ecfd2c3a31b42b380c593aef0bbc23775874cc7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076819"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Naplnění datové sady z adaptéru dat
[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataSet> Rezidentní reprezentace dat, které poskytuje konzistentní relační programovací model bez ohledu na zdroj dat je. `DataSet` Představuje ucelenou sadu dat, která obsahuje tabulky, omezení a relace mezi tabulkami. Protože `DataSet` je nezávislý na zdroji dat `DataSet` může obsahovat místní aplikaci a data z různých zdrojů dat. Interakce s stávajících zdrojů dat je řízen pomocí `DataAdapter`.  
  
 `SelectCommand` Vlastnost `DataAdapter` je `Command` objekt, který načítá data z datového zdroje. `InsertCommand`, `UpdateCommand`, A `DeleteCommand` vlastnosti `DataAdapter` jsou `Command` objekty, které spravují aktualizace dat ve zdroji dat podle změny provedené v datech v `DataSet`. Tyto vlastnosti se budeme věnovat jednotlivě podrobněji v [aktualizace zdroje dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 `Fill` Metodu `DataAdapter` slouží k naplnění `DataSet` s výsledky `SelectCommand` z `DataAdapter`. `Fill` jako argumenty přijímá `DataSet` vyplní a `DataTable` objekt nebo název `DataTable` tankujeme řádků vrácených `SelectCommand`.  
  
> [!NOTE]
>  Použití `DataAdapter` chcete načíst všechny tabulky trvá určitou dobu, zejména v případě, že existují mnoho řádků v tabulce. Důvodem je, že přístup k databázi, lokalizuje a zpracování dat, a následný přenos dat do klienta je časově náročné. Všechny tabulky potažením prstem klienta zamkne také všechny řádky na serveru. Chcete-li zvýšit výkon, můžete použít `WHERE` klauzule, která výrazně snížit počet řádků vrácených do klienta. Může také snížit množství dat vrácených do klienta pouze explicitně uvedete seznam požadovaných sloupců v `SELECT` příkazu. Další dobrá alternativním řešením je načíst řádky v dávkách (například několik stovek řádků najednou) a další dávku načíst pouze po dokončení aktuální dávkou klienta.  
  
 `Fill` Metoda používá `DataReader` objekt implicitně vrátí názvy sloupců a typy, které se používají k vytváření tabulek v `DataSet`a dat k vyplnění řádků tabulky v `DataSet`. Tabulky a sloupce jsou vytvářeny, pouze pokud ještě splněné nejsou; v opačném případě `Fill` používá stávající `DataSet` schématu. Typy sloupců vytvořených jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy podle tabulky v [mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md). Primární klíče se nevytvoří, pokud existují ve zdroji dat a `DataAdapter` **.**`MissingSchemaAction` je nastavena na `MissingSchemaAction` **.** `AddWithKey`. Pokud `Fill` zjistí, že primární klíč pro tabulku existuje, přepíše data v `DataSet` s daty ze zdroje dat pro řádky, kde se hodnoty pro sloupec primárního klíče shodují řádku vrácená ze zdroje dat. Pokud se nenajde žádný primární klíč, data se připojí k tabulkám ve `DataSet`. `Fill` používá všechna mapování, které mohou existovat při naplňování `DataSet` (naleznete v tématu [adaptéru dat, datové tabulky a DataColumn mapování](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
>  Pokud `SelectCommand` vrátí výsledky z vnějšího spojení, `DataAdapter` nenastaví `PrimaryKey` hodnoty pro výsledné `DataTable`. Je nutné definovat `PrimaryKey` sami, abyste měli jistotu, že jsou správně přeložit duplicitní řádky. Další informace najdete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Následující příklad kódu vytvoří instanci <xref:System.Data.SqlClient.SqlDataAdapter> , která používá <xref:System.Data.SqlClient.SqlConnection> Microsoft SQL Server `Northwind` databáze a naplní <xref:System.Data.DataTable> v `DataSet` s seznam zákazníků. Příkaz jazyka SQL a <xref:System.Data.SqlClient.SqlConnection> argumenty předané <xref:System.Data.SqlClient.SqlDataAdapter> konstruktoru se používají k vytváření <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> vlastnost <xref:System.Data.SqlClient.SqlDataAdapter>.  
  
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
>  Kód v tomto příkladu se neotevře explicitně a zavřít `Connection`. `Fill` Metoda implicitně otevře `Connection` , který `DataAdapter` používá, pokud zjistí, že připojení ještě není otevřený. Pokud `Fill` otevření připojení, také uzavře připojení při `Fill` bylo dokončeno. Při řešení pomocí jedné operace, jako to může zjednodušit kódu `Fill` nebo `Update`. Nicméně pokud provádíte více operací, které vyžaduje otevřené připojení, lze zvýšit výkon vaší aplikace explicitně voláním `Open` metodu `Connection`, provádění operací na zdroji dat, a následným voláním `Close` metodu `Connection`. Doporučujeme nechat připojení ke zdroji dat otevřené jako stručně k uvolnění prostředků pro použití v jiné klientské aplikace.  
  
## <a name="multiple-result-sets"></a>Více sad výsledků dotazu  
 Pokud `DataAdapter` zjistí sady více výsledků, vytvoří více tabulek v `DataSet`. V tabulkách jsou uvedeny na přírůstkové výchozí název tabulky*N*počínaje "Table" pro Table0. Pokud zadáte název tabulky je předán jako argument `Fill` metody v tabulkách jsou uvedeny přírůstkové výchozí název TableName*N*počínaje "TableName" pro TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Naplnění datové sady z více adaptérů dat  
 Libovolný počet `DataAdapter` objekty je možné s `DataSet`. Každý `DataAdapter` slouží k vyplnění jeden nebo více `DataTable` objekty a vyřešit aktualizací zpět do zdroje relevantní data. `DataRelation` a `Constraint` objekty mohou být přidány do `DataSet` místně, což vám umožní se vztahují data z různorodých datových zdrojů. Například `DataSet` může obsahovat data z databáze Microsoft SQL Server, databázi IBM DB2 prostřednictvím OLE DB a zdroj dat, která jsou streamována XML. Jeden nebo více `DataAdapter` objekty zvládne komunikace pro jednotlivé zdroje dat.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu naplní seznam zákazníků `Northwind` databáze na serveru Microsoft SQL Server a seznam objednávek z `Northwind` databáze uloženou v aplikaci Microsoft Access 2000. Vyplněný tabulky souvisejí s `DataRelation`, a pak zobrazí seznam zákazníků s objednávek tohoto zákazníka. Další informace o `DataRelation` objekty, najdete [přidání datových relací](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) a [procházení datových relací](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).  
  
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
  
## <a name="sql-server-decimal-type"></a>Typ desetinné SQL serveru  
 Ve výchozím nastavení `DataSet` ukládá data s využitím [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] datové typy. Pro většinu aplikací tyto poskytují pohodlný reprezentace informace o zdroji dat. Tento zápis však může dojít k potížím, pokud datový typ ve zdroji dat je desítkový nebo číselný datový typ SQL serveru. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` Datový typ povoluje maximálně 28 platných číslic, zatímco SQL Server `decimal` datový typ umožňuje 38 nejvýznamnějších číslic. Pokud `SqlDataAdapter` určuje během `Fill` operace, která přesnost systému SQL Server `decimal` pole je větší než 28 znaků, aktuální řádek není přidán do `DataTable`. Místo toho `FillError` dojde k události, což vám umožní zjistit, jestli ke ztrátě přesnosti dojít a reagují odpovídajícím způsobem. Další informace o `FillError` událostí, naleznete v tématu [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md). Získat SQL Server `decimal` hodnotu, můžete použít také <xref:System.Data.SqlClient.SqlDataReader> objektu a volání <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> metoda.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 zavedl rozšířenou podporu <xref:System.Data.SqlTypes> v `DataSet`. Další informace najdete v tématu [SqlTypes a datová sada](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB kapitol  
 Hierarchické sady řádků nebo kapitol (typ OLE DB `DBTYPE_HCHAPTER`, typ ADO `adChapter`) můžete použít tak, aby vyplnil obsah `DataSet`. Při <xref:System.Data.OleDb.OleDbDataAdapter> zaznamená sloupec nepoužívaly kapitoly během `Fill` operace, `DataTable` pro sloupec nepoužívaly kapitoly, se vytvoří a je tuto tabulku se sloupci a řádky v kapitole. Tabulky vytvořené pro nepoužívaly kapitoly sloupec nazýval pomocí název nadřazené tabulky a název sloupce nepoužívaly kapitoly ve formě "*ParentTableNameChapteredColumnName*". Pokud tabulka již existuje v `DataSet` , který odpovídá názvu nepoužívaly kapitoly sloupec, v aktuální tabulce je naplněný daty kapitoly. Pokud neexistuje žádný sloupec z existující tabulky, který odpovídá sloupci najít v kapitole, je přidán nový sloupec.  
  
 Před tabulky v `DataSet` jsou vyplněny s daty v nepoužívaly kapitoly sloupce, relace se vytvoří mezi nadřazenými a podřízenými tabulek v hierarchické sadě řádků tak, že přidáte sloupec celých čísel do nadřazené i podřízené tabulky, nastavení nadřazeného sloupce Automatické zvyšování čísla a vytváření `DataRelation` pomocí přidání sloupce z obou tabulek. Přidání vztahu je pojmenováno pomocí nadřazeného názvy sloupců tabulky a kapitoly ve formě "*ParentTableNameChapterColumnName*".  
  
 Všimněte si, že související sloupec existuje pouze v `DataSet`. Následné výplně ze zdroje dat může způsobit nové řádky, které chcete přidat do tabulky místo změny do existující řádky.  
  
 Všimněte si také, že pokud použijete `DataAdapter.Fill` přetížení, které přijímá `DataTable`, bude vyplněno pouze tuto tabulku. Sloupec celých čísel automatické zvyšování bude i tak přidána k tabulce, ale žádné podřízené tabulce bude vytvořen nebo vyplněné a se nevytvoří žádný vztah.  
  
 Následující příklad používá zprostředkovatele MSDataShape ke generování objednávek pro každého zákazníka neočekávaný sloupec kapitoly v seznam zákazníků. A `DataSet` pak naplní daty.  
  
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
  
 Když `Fill` operace se dokončila, `DataSet` obsahuje dvě tabulky: `Customers` a `CustomersOrders`, kde `CustomersOrders` představuje sloupci nepoužívaly kapitoly. Další sloupec s názvem `Orders` se přidá do `Customers` tabulku a sloupec s názvem `CustomersOrders` se přidá do `CustomersOrders` tabulky. `Orders` Sloupec `Customers` tabulky je nastavena na automatické zvyšování čísla. A `DataRelation`, `CustomersOrders`, se vytvoří s použitím sloupce, které byly přidány do tabulky s `Customers` jako nadřazená tabulka. Následující tabulky popisují některé ukázkové výsledky.  
  
### <a name="tablename-customers"></a>Název tabulky: Zákazníci  
  
|ID zákazníka|CompanyName|Objednávky|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Helados Ana Trujillo Emparedados y|1|  
  
### <a name="tablename-customersorders"></a>Název tabulky: CustomersOrders  
  
|ID zákazníka|ID objednávky|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Viz také:

- [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [Úpravy dat přes DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [Více aktivních sad výsledků (MARS)](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
