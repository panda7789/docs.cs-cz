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
# <a name="populating-a-dataset-from-a-dataadapter"></a><span data-ttu-id="fbc00-103">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="fbc00-103">Populating a DataSet from a DataAdapter</span></span>
<span data-ttu-id="fbc00-104">ADO.NET <xref:System.Data.DataSet> je reprezentace dat rezidenta v paměti, která poskytuje konzistentní relační programovací model nezávislý na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="fbc00-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model independent of the data source.</span></span> <span data-ttu-id="fbc00-105">`DataSet`Představuje kompletní sadu dat, která zahrnuje tabulky, omezení a vztahy mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="fbc00-105">The `DataSet` represents a complete set of data that includes tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="fbc00-106">Vzhledem k tomu `DataSet` , že je nezávislý na zdroji dat, `DataSet` může do aplikace zahrnout data místní a data z více zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="fbc00-106">Because the `DataSet` is independent of the data source, a `DataSet` can include data local to the application, and data from multiple data sources.</span></span> <span data-ttu-id="fbc00-107">Interakce s existujícími zdroji dat je řízena prostřednictvím `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-107">Interaction with existing data sources is controlled through the `DataAdapter`.</span></span>  
  
 <span data-ttu-id="fbc00-108">`SelectCommand`Vlastnost `DataAdapter` je `Command` objekt, který načítá data ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="fbc00-108">The `SelectCommand` property of the `DataAdapter` is a `Command` object that retrieves data from the data source.</span></span> <span data-ttu-id="fbc00-109">`InsertCommand`Vlastnosti, `UpdateCommand` a `DeleteCommand` `DataAdapter` jsou `Command` objekty, které spravují aktualizace dat ve zdroji dat v souladu s úpravami provedenými v datech v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-109">The `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of the `DataAdapter` are `Command` objects that manage updates to the data in the data source according to modifications made to the data in the `DataSet`.</span></span> <span data-ttu-id="fbc00-110">Tyto vlastnosti jsou podrobněji popsány v části [aktualizace zdrojů dat pomocí datových adaptérů](updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="fbc00-110">These properties are covered in more detail in [Updating Data Sources with DataAdapters](updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="fbc00-111">`Fill`Metoda `DataAdapter` je použita k naplnění výsledků z `DataSet` `SelectCommand` `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-111">The `Fill` method of the `DataAdapter` is used to populate a `DataSet` with the results of the `SelectCommand` of the `DataAdapter`.</span></span> <span data-ttu-id="fbc00-112">`Fill`přijímá jako argumenty a `DataSet` k naplnění, `DataTable` objekt nebo název, který `DataTable` má být vyplněn řádky vrácenými z `SelectCommand` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-112">`Fill` takes as its arguments a `DataSet` to be populated, and a `DataTable` object, or the name of the `DataTable` to be filled with the rows returned from the `SelectCommand`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbc00-113">Použití `DataAdapter` pro načtení všech tabulek vybere čas, zejména v případě, že je v tabulce mnoho řádků.</span><span class="sxs-lookup"><span data-stu-id="fbc00-113">Using the `DataAdapter` to retrieve all of a table takes time, especially if there are many rows in the table.</span></span> <span data-ttu-id="fbc00-114">Důvodem je to, že přístup k databázi, vyhledání a zpracování dat a následné přenos dat do klienta je časově náročný.</span><span class="sxs-lookup"><span data-stu-id="fbc00-114">This is because accessing the database, locating and processing the data, and then transferring the data to the client is time-consuming.</span></span> <span data-ttu-id="fbc00-115">Když se všechny tabulky nastahují do klienta, zamkne se i všechny řádky na serveru.</span><span class="sxs-lookup"><span data-stu-id="fbc00-115">Pulling all of the table to the client also locks all of the rows on the server.</span></span> <span data-ttu-id="fbc00-116">Chcete-li zvýšit výkon, můžete použít `WHERE` klauzuli k výraznému snížení počtu řádků vrácených klientovi.</span><span class="sxs-lookup"><span data-stu-id="fbc00-116">To improve performance, you can use the `WHERE` clause to greatly reduce the number of rows returned to the client.</span></span> <span data-ttu-id="fbc00-117">Množství dat vrácených klientovi můžete také omezit pouze explicitně uvedením požadovaných sloupců v `SELECT` příkazu.</span><span class="sxs-lookup"><span data-stu-id="fbc00-117">You can also reduce the amount of data returned to the client by only explicitly listing required columns in the `SELECT` statement.</span></span> <span data-ttu-id="fbc00-118">Dalším dobrým řešením je načíst řádky v dávkách (například několik stovky řádků najednou) a načíst další dávku pouze v případě, že je klient dokončen s aktuální dávkou.</span><span class="sxs-lookup"><span data-stu-id="fbc00-118">Another good workaround is to retrieve the rows in batches (such as several hundred rows at a time) and only retrieve the next batch when the client is finished with the current batch.</span></span>  
  
 <span data-ttu-id="fbc00-119">`Fill`Metoda používá `DataReader` objekt implicitně k vrácení názvů sloupců a typů, které se používají k vytvoření tabulky v nástroji `DataSet` , a data k naplnění řádků tabulek v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-119">The `Fill` method uses the `DataReader` object implicitly to return the column names and types that are used to create the tables in the `DataSet`, and the data to populate the rows of the tables in the `DataSet`.</span></span> <span data-ttu-id="fbc00-120">Tabulky a sloupce jsou vytvořeny pouze v případě, že ještě neexistují; v opačném případě `Fill` použije existující `DataSet` schéma.</span><span class="sxs-lookup"><span data-stu-id="fbc00-120">Tables and columns are only created if they do not already exist; otherwise `Fill` uses the existing `DataSet` schema.</span></span> <span data-ttu-id="fbc00-121">Typy sloupců jsou vytvořeny jako .NET Framework typy podle tabulek v [mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="fbc00-121">Column types are created as .NET Framework types according to the tables in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span> <span data-ttu-id="fbc00-122">Primární klíče se nevytvoří, pokud ve zdroji dat neexistují `DataAdapter` **.**`MissingSchemaAction`</span><span class="sxs-lookup"><span data-stu-id="fbc00-122">Primary keys are not created unless they exist in the data source and `DataAdapter`**.**`MissingSchemaAction`</span></span> <span data-ttu-id="fbc00-123">je nastaven na `MissingSchemaAction` **.** `AddWithKey` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-123">is set to `MissingSchemaAction`**.**`AddWithKey`.</span></span> <span data-ttu-id="fbc00-124">Pokud aplikace `Fill` zjistí, že primární klíč pro tabulku existuje, přepíše data v `DataSet` datech ze zdroje dat pro řádky, ve kterých se hodnoty sloupce primárního klíče shodují s hodnotami vrácenými ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="fbc00-124">If `Fill` finds that a primary key exists for a table, it will overwrite data in the `DataSet` with data from the data source for rows where the primary key column values match those of the row returned from the data source.</span></span> <span data-ttu-id="fbc00-125">Pokud se nenajde žádný primární klíč, data se připojí k tabulkám v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-125">If no primary key is found, the data is appended to the tables in the `DataSet`.</span></span> <span data-ttu-id="fbc00-126">`Fill`používá všechna mapování, která mohou existovat při naplňování `DataSet` (viz [DataAdapter DataTable a DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).</span><span class="sxs-lookup"><span data-stu-id="fbc00-126">`Fill` uses any mappings that may exist when you populate the `DataSet` (see [DataAdapter DataTable and DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbc00-127">Vrátí-li `SelectCommand` funkce výsledky vnějšího spojení, `DataAdapter` nenastaví `PrimaryKey` hodnotu pro výsledný výsledek `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-127">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` does not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="fbc00-128">Abyste měli `PrimaryKey` jistotu, že se duplicitní řádky vyřeší správně, musíte definovat sami sebe.</span><span class="sxs-lookup"><span data-stu-id="fbc00-128">You must define the `PrimaryKey` yourself to make sure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="fbc00-129">Další informace najdete v tématu [Definování primárních klíčů](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="fbc00-129">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="fbc00-130">Následující příklad kódu vytvoří instanci <xref:System.Data.SqlClient.SqlDataAdapter> , která používá <xref:System.Data.SqlClient.SqlConnection> k Microsoft SQL Server `Northwind` databázi a naplní <xref:System.Data.DataTable> `DataSet` ji seznamem zákazníků.</span><span class="sxs-lookup"><span data-stu-id="fbc00-130">The following code example creates an instance of a <xref:System.Data.SqlClient.SqlDataAdapter> that uses a <xref:System.Data.SqlClient.SqlConnection> to the Microsoft SQL Server `Northwind` database and populates a <xref:System.Data.DataTable> in a `DataSet` with the list of customers.</span></span> <span data-ttu-id="fbc00-131">Příkaz jazyka SQL a <xref:System.Data.SqlClient.SqlConnection> argumenty předané <xref:System.Data.SqlClient.SqlDataAdapter> konstruktoru jsou použity k vytvoření <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> vlastnosti <xref:System.Data.SqlClient.SqlDataAdapter> .</span><span class="sxs-lookup"><span data-stu-id="fbc00-131">The SQL statement and <xref:System.Data.SqlClient.SqlConnection> arguments passed to the <xref:System.Data.SqlClient.SqlDataAdapter> constructor are used to create the <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> property of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbc00-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="fbc00-132">Example</span></span>  
  
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
> <span data-ttu-id="fbc00-133">Kód zobrazený v tomto příkladu explicitně neotevře a neuzavře `Connection` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-133">The code shown in this example does not explicitly open and close the `Connection`.</span></span> <span data-ttu-id="fbc00-134">`Fill`Metoda implicitně otevře rozhraní `Connection` , které používá, `DataAdapter` Pokud zjistí, že připojení již není otevřeno.</span><span class="sxs-lookup"><span data-stu-id="fbc00-134">The `Fill` method implicitly opens the `Connection` that the `DataAdapter` is using if it finds that the connection is not already open.</span></span> <span data-ttu-id="fbc00-135">Pokud `Fill` se připojení otevřelo, ukončí se i po `Fill` dokončení připojení.</span><span class="sxs-lookup"><span data-stu-id="fbc00-135">If `Fill` opened the connection, it also closes the connection when `Fill` is finished.</span></span> <span data-ttu-id="fbc00-136">To může zjednodušit váš kód při práci s jednou operací, jako je například `Fill` nebo `Update` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-136">This can simplify your code when you deal with a single operation such as a `Fill` or an `Update`.</span></span> <span data-ttu-id="fbc00-137">Pokud však provádíte více operací, které vyžadují otevřené připojení, můžete zvýšit výkon aplikace explicitním voláním `Open` metody `Connection` , provedení operací proti zdroji dat a následným voláním `Close` metody `Connection` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-137">However, if you are performing multiple operations that require an open connection, you can improve the performance of your application by explicitly calling the `Open` method of the `Connection`, performing the operations against the data source, and then calling the `Close` method of the `Connection`.</span></span> <span data-ttu-id="fbc00-138">Měli byste se pokusit o udržování připojení ke zdroji dat co nejdříve, pokud chcete uvolnit prostředky pro použití jinými klientskými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="fbc00-138">You should try to keep connections to the data source open as briefly as possible to free resources for use by other client applications.</span></span>  
  
## <a name="multiple-result-sets"></a><span data-ttu-id="fbc00-139">Více sad výsledků</span><span class="sxs-lookup"><span data-stu-id="fbc00-139">Multiple Result Sets</span></span>  
 <span data-ttu-id="fbc00-140">Pokud `DataAdapter` dojde k více výsledkům sady výsledků, vytvoří se několik tabulek v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-140">If the `DataAdapter` encounters multiple result sets, it creates multiple tables in the `DataSet`.</span></span> <span data-ttu-id="fbc00-141">Tabulkám se předává přírůstkový výchozí název tabulky*N*, od "Table" pro TABLE0.</span><span class="sxs-lookup"><span data-stu-id="fbc00-141">The tables are given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span> <span data-ttu-id="fbc00-142">Pokud je název tabulky předán jako argument pro `Fill` metodu, tabulky jsou předány přírůstkovým výchozím názvem TableName*N*, počínaje hodnotou "TableName" pro TableName0.</span><span class="sxs-lookup"><span data-stu-id="fbc00-142">If a table name is passed as an argument to the `Fill` method, the tables are given an incremental default name of TableName*N*, starting with "TableName" for TableName0.</span></span>  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a><span data-ttu-id="fbc00-143">Naplnění datové sady z více datových adaptérů</span><span class="sxs-lookup"><span data-stu-id="fbc00-143">Populating a DataSet from Multiple DataAdapters</span></span>  
 <span data-ttu-id="fbc00-144">Libovolný počet `DataAdapter` objektů lze použít s `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-144">Any number of `DataAdapter` objects can be used with a `DataSet`.</span></span> <span data-ttu-id="fbc00-145">Každý `DataAdapter` lze použít k vyplnění jednoho nebo více `DataTable` objektů a vyřešení aktualizací zpět na relevantní zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="fbc00-145">Each `DataAdapter` can be used to fill one or more `DataTable` objects and resolve updates back to the relevant data source.</span></span> <span data-ttu-id="fbc00-146">`DataRelation`objekty a je `Constraint` možné přidávat `DataSet` místně, což umožňuje propojit data z odlišných zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="fbc00-146">`DataRelation` and `Constraint` objects can be added to the `DataSet` locally, which enables you to relate data from dissimilar data sources.</span></span> <span data-ttu-id="fbc00-147">`DataSet`Může například obsahovat data z databáze Microsoft SQL Server, databázi IBM DB2 zveřejněnou prostřednictvím OLE DB a zdroj dat, který streamuje XML.</span><span class="sxs-lookup"><span data-stu-id="fbc00-147">For example, a `DataSet` can contain data from a Microsoft SQL Server database, an IBM DB2 database exposed through OLE DB, and a data source that streams XML.</span></span> <span data-ttu-id="fbc00-148">Jeden nebo více `DataAdapter` objektů může zpracovávat komunikaci s každým zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="fbc00-148">One or more `DataAdapter` objects can handle communication to each data source.</span></span>  
  
### <a name="example"></a><span data-ttu-id="fbc00-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="fbc00-149">Example</span></span>  
 <span data-ttu-id="fbc00-150">Následující příklad kódu naplní seznam zákazníků z `Northwind` databáze na Microsoft SQL Server a seznam objednávek z `Northwind` databáze uložené v aplikaci Microsoft Access 2000.</span><span class="sxs-lookup"><span data-stu-id="fbc00-150">The following code example populates a list of customers from the `Northwind` database on Microsoft SQL Server, and a list of orders from the `Northwind` database stored in Microsoft Access 2000.</span></span> <span data-ttu-id="fbc00-151">Vyplněné tabulky se vztahují k `DataRelation` a seznam zákazníků se pak zobrazí s objednávkami daného zákazníka.</span><span class="sxs-lookup"><span data-stu-id="fbc00-151">The filled tables are related with a `DataRelation`, and the list of customers is then displayed with the orders for that customer.</span></span> <span data-ttu-id="fbc00-152">Další informace o `DataRelation` objektech naleznete v tématu [Přidání datových vztahů](./dataset-datatable-dataview/adding-datarelations.md) a navigace v datových [vztazích](./dataset-datatable-dataview/navigating-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="fbc00-152">For more information about `DataRelation` objects, see [Adding DataRelations](./dataset-datatable-dataview/adding-datarelations.md) and [Navigating DataRelations](./dataset-datatable-dataview/navigating-datarelations.md).</span></span>  
  
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
  
## <a name="sql-server-decimal-type"></a><span data-ttu-id="fbc00-153">SQL Server Typ Decimal</span><span class="sxs-lookup"><span data-stu-id="fbc00-153">SQL Server Decimal Type</span></span>  
 <span data-ttu-id="fbc00-154">Ve výchozím nastavení `DataSet` ukládá data pomocí .NET Framework datových typů.</span><span class="sxs-lookup"><span data-stu-id="fbc00-154">By default, the `DataSet` stores data by using .NET Framework data types.</span></span> <span data-ttu-id="fbc00-155">Pro většinu aplikací poskytují tyto informace užitečné znázornění informací o zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="fbc00-155">For most applications, these provide a convenient representation of data source information.</span></span> <span data-ttu-id="fbc00-156">Tato reprezentace ale může způsobit potíže, pokud je datový typ ve zdroji dat SQL Server desítkový nebo číselný datový typ.</span><span class="sxs-lookup"><span data-stu-id="fbc00-156">However, this representation may cause a problem when the data type in the data source is a SQL Server decimal or numeric data type.</span></span> <span data-ttu-id="fbc00-157">`decimal`Datový typ .NET Framework umožňuje maximálně 28 platných číslic, zatímco `decimal` datový typ SQL Server umožňuje 38 platných číslic.</span><span class="sxs-lookup"><span data-stu-id="fbc00-157">The .NET Framework `decimal` data type allows a maximum of 28 significant digits, whereas the SQL Server `decimal` data type allows 38 significant digits.</span></span> <span data-ttu-id="fbc00-158">Pokud v rámci `SqlDataAdapter` operace určíte `Fill` , že přesnost SQL Serverho `decimal` pole je větší než 28 znaků, aktuální řádek není přidán do `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-158">If the `SqlDataAdapter` determines during a `Fill` operation that the precision of a SQL Server `decimal` field is larger than 28 characters, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="fbc00-159">Místo toho `FillError` dojde k události, která umožňuje určit, zda dojde ke ztrátě přesnosti, a odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="fbc00-159">Instead the `FillError` event occurs, which enables you to determine whether a loss of precision will occur, and respond appropriately.</span></span> <span data-ttu-id="fbc00-160">Další informace o `FillError` události naleznete v tématu [zpracování událostí DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="fbc00-160">For more information about the `FillError` event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span> <span data-ttu-id="fbc00-161">Chcete-li získat SQL Server `decimal` hodnotu, můžete také použít <xref:System.Data.SqlClient.SqlDataReader> objekt a volat <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="fbc00-161">To get the SQL Server `decimal` value, you can also use a <xref:System.Data.SqlClient.SqlDataReader> object and call the <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> method.</span></span>  
  
 <span data-ttu-id="fbc00-162">ADO.NET 2,0 představil rozšířenou podporu pro <xref:System.Data.SqlTypes> v nástroji `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-162">ADO.NET 2.0 introduced enhanced support for <xref:System.Data.SqlTypes> in the `DataSet`.</span></span> <span data-ttu-id="fbc00-163">Další informace naleznete v tématu [SqlTypes a DataSet](./sql/sqltypes-and-the-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="fbc00-163">For more information, see [SqlTypes and the DataSet](./sql/sqltypes-and-the-dataset.md).</span></span>  
  
## <a name="ole-db-chapters"></a><span data-ttu-id="fbc00-164">OLE DB kapitoly</span><span class="sxs-lookup"><span data-stu-id="fbc00-164">OLE DB Chapters</span></span>  
 <span data-ttu-id="fbc00-165">Hierarchické sady řádků nebo kapitoly (typ OLE DB `DBTYPE_HCHAPTER` , typ ADO `adChapter` ) lze použít k vyplnění obsahu `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-165">Hierarchical rowsets, or chapters (OLE DB type `DBTYPE_HCHAPTER`, ADO type `adChapter`) can be used to fill the contents of a `DataSet`.</span></span> <span data-ttu-id="fbc00-166">Když <xref:System.Data.OleDb.OleDbDataAdapter> dojde k vyplňování sloupce v kapitole v rámci `Fill` operace, vytvoří `DataTable` se pro sloupec kapitoly a tato tabulka se vyplní sloupci a řádky z této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="fbc00-166">When the <xref:System.Data.OleDb.OleDbDataAdapter> encounters a chaptered column during a `Fill` operation, a `DataTable` is created for the chaptered column, and that table is filled with the columns and rows from the chapter.</span></span> <span data-ttu-id="fbc00-167">Tabulka vytvořená pro sloupec s názvem kapitoly je pojmenována pomocí názvu nadřazené tabulky a názvu sloupce kapitoly ve formátu "*ParentTableNameChapteredColumnName*".</span><span class="sxs-lookup"><span data-stu-id="fbc00-167">The table created for the chaptered column is named by using both the parent table name and the chaptered column name in the form "*ParentTableNameChapteredColumnName*".</span></span> <span data-ttu-id="fbc00-168">Pokud tabulka již existuje v `DataSet` , která se shoduje s názvem sloupce v kapitole, je aktuální tabulka doplněna daty kapitoly.</span><span class="sxs-lookup"><span data-stu-id="fbc00-168">If a table already exists in the `DataSet` that matches the name of the chaptered column, the current table is filled with the chapter data.</span></span> <span data-ttu-id="fbc00-169">Pokud v existující tabulce není žádný sloupec, který by odpovídal sloupci nalezenému v této kapitole, je přidán nový sloupec.</span><span class="sxs-lookup"><span data-stu-id="fbc00-169">If there is no column in an existing table that matches a column found in the chapter, a new column is added.</span></span>  
  
 <span data-ttu-id="fbc00-170">Předtím, než jsou tabulky v poli `DataSet` vyplněny daty ze sloupců v poli kapitoly, je vytvořena relace mezi nadřazenými a podřízenými tabulkami hierarchické sady řádků přidáním celého čísla do nadřazené a podřízené tabulky, nastavením nadřazeného sloupce na Automatický přírůstek a vytvořením `DataRelation` pomocí přidaných sloupců z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="fbc00-170">Before the tables in the `DataSet` are filled with the data in the chaptered columns, a relation is created between the parent and child tables of the hierarchical rowset by adding an integer column to both the parent and child table, setting the parent column to auto-increment, and creating a `DataRelation` using the added columns from both tables.</span></span> <span data-ttu-id="fbc00-171">Přidaný vztah je pojmenován pomocí nadřazené tabulky a názvů sloupců kapitoly ve formátu "*ParentTableNameChapterColumnName*".</span><span class="sxs-lookup"><span data-stu-id="fbc00-171">The added relation is named by using the parent table and chapter column names in the form "*ParentTableNameChapterColumnName*".</span></span>  
  
 <span data-ttu-id="fbc00-172">Všimněte si, že související sloupec existuje pouze v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-172">Note that the related column only exists in the `DataSet`.</span></span> <span data-ttu-id="fbc00-173">Další výplně ze zdroje dat mohou způsobit, že se do tabulek přidají nové řádky místo sloučení změn do stávajících řádků.</span><span class="sxs-lookup"><span data-stu-id="fbc00-173">Subsequent fills from the data source can cause new rows to be added to the tables instead of changes being merged into existing rows.</span></span>  
  
 <span data-ttu-id="fbc00-174">Všimněte si také, že pokud použijete `DataAdapter.Fill` přetížení, které používá `DataTable` , bude vyplněno pouze tato tabulka.</span><span class="sxs-lookup"><span data-stu-id="fbc00-174">Note also that, if you use the `DataAdapter.Fill` overload that takes a `DataTable`, only that table will be filled.</span></span> <span data-ttu-id="fbc00-175">Do tabulky bude stále přidán sloupec s automatickým přírůstkovým celým číslem, ale nebude vytvořena ani žádná podřízená tabulka a nebude vytvořena žádná relace.</span><span class="sxs-lookup"><span data-stu-id="fbc00-175">An auto-incrementing integer column will still be added to the table, but no child table will be created or filled, and no relation will be created.</span></span>  
  
 <span data-ttu-id="fbc00-176">Následující příklad používá poskytovatele MSDataShape k vygenerování sloupce kapitoly objednávek pro každého zákazníka v seznamu zákazníků.</span><span class="sxs-lookup"><span data-stu-id="fbc00-176">The following example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span> <span data-ttu-id="fbc00-177">A `DataSet` pak se vyplní daty.</span><span class="sxs-lookup"><span data-stu-id="fbc00-177">A `DataSet` is then filled with the data.</span></span>  
  
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
  
 <span data-ttu-id="fbc00-178">Po `Fill` dokončení operace `DataSet` obsahuje dvě tabulky: `Customers` a `CustomersOrders` , kde `CustomersOrders` představuje sloupec v kapitolě.</span><span class="sxs-lookup"><span data-stu-id="fbc00-178">When the `Fill` operation is complete, the `DataSet` contains two tables: `Customers` and `CustomersOrders`, where `CustomersOrders` represents the chaptered column.</span></span> <span data-ttu-id="fbc00-179">`Orders`Do tabulky se přidá další sloupec s názvem `Customers` a `CustomersOrders` do tabulky se přidá další sloupec s názvem `CustomersOrders` .</span><span class="sxs-lookup"><span data-stu-id="fbc00-179">An additional column named `Orders` is added to the `Customers` table, and an additional column named `CustomersOrders` is added to the `CustomersOrders` table.</span></span> <span data-ttu-id="fbc00-180">`Orders`Sloupec v `Customers` tabulce je nastaven na hodnotu Automatický přírůstek.</span><span class="sxs-lookup"><span data-stu-id="fbc00-180">The `Orders` column in the `Customers` table is set to auto-increment.</span></span> <span data-ttu-id="fbc00-181">A `DataRelation` , `CustomersOrders` , je vytvořen pomocí sloupců, které byly přidány do tabulek s `Customers` jako nadřazenou tabulkou.</span><span class="sxs-lookup"><span data-stu-id="fbc00-181">A `DataRelation`, `CustomersOrders`, is created by using the columns that were added to the tables with `Customers` as the parent table.</span></span> <span data-ttu-id="fbc00-182">V následujících tabulkách jsou uvedeny některé příklady výsledků.</span><span class="sxs-lookup"><span data-stu-id="fbc00-182">The following tables show some sample results.</span></span>  
  
### <a name="tablename-customers"></a><span data-ttu-id="fbc00-183">TableName: zákazníci</span><span class="sxs-lookup"><span data-stu-id="fbc00-183">TableName: Customers</span></span>  
  
|<span data-ttu-id="fbc00-184">CustomerID</span><span class="sxs-lookup"><span data-stu-id="fbc00-184">CustomerID</span></span>|<span data-ttu-id="fbc00-185">CompanyName</span><span class="sxs-lookup"><span data-stu-id="fbc00-185">CompanyName</span></span>|<span data-ttu-id="fbc00-186">Orders</span><span class="sxs-lookup"><span data-stu-id="fbc00-186">Orders</span></span>|  
|----------------|-----------------|------------|  
|<span data-ttu-id="fbc00-187">ALFKI</span><span class="sxs-lookup"><span data-stu-id="fbc00-187">ALFKI</span></span>|<span data-ttu-id="fbc00-188">Alfreds Futterkiste</span><span class="sxs-lookup"><span data-stu-id="fbc00-188">Alfreds Futterkiste</span></span>|<span data-ttu-id="fbc00-189">0</span><span class="sxs-lookup"><span data-stu-id="fbc00-189">0</span></span>|  
|<span data-ttu-id="fbc00-190">ANATR</span><span class="sxs-lookup"><span data-stu-id="fbc00-190">ANATR</span></span>|<span data-ttu-id="fbc00-191">Ana Trujillo Emparedados y Helados</span><span class="sxs-lookup"><span data-stu-id="fbc00-191">Ana Trujillo Emparedados y helados</span></span>|<span data-ttu-id="fbc00-192">1</span><span class="sxs-lookup"><span data-stu-id="fbc00-192">1</span></span>|  
  
### <a name="tablename-customersorders"></a><span data-ttu-id="fbc00-193">TableName: CustomersOrders</span><span class="sxs-lookup"><span data-stu-id="fbc00-193">TableName: CustomersOrders</span></span>  
  
|<span data-ttu-id="fbc00-194">CustomerID</span><span class="sxs-lookup"><span data-stu-id="fbc00-194">CustomerID</span></span>|<span data-ttu-id="fbc00-195">OrderID</span><span class="sxs-lookup"><span data-stu-id="fbc00-195">OrderID</span></span>|<span data-ttu-id="fbc00-196">CustomersOrders</span><span class="sxs-lookup"><span data-stu-id="fbc00-196">CustomersOrders</span></span>|  
|----------------|-------------|---------------------|  
|<span data-ttu-id="fbc00-197">ALFKI</span><span class="sxs-lookup"><span data-stu-id="fbc00-197">ALFKI</span></span>|<span data-ttu-id="fbc00-198">10643</span><span class="sxs-lookup"><span data-stu-id="fbc00-198">10643</span></span>|<span data-ttu-id="fbc00-199">0</span><span class="sxs-lookup"><span data-stu-id="fbc00-199">0</span></span>|  
|<span data-ttu-id="fbc00-200">ALFKI</span><span class="sxs-lookup"><span data-stu-id="fbc00-200">ALFKI</span></span>|<span data-ttu-id="fbc00-201">10692</span><span class="sxs-lookup"><span data-stu-id="fbc00-201">10692</span></span>|<span data-ttu-id="fbc00-202">0</span><span class="sxs-lookup"><span data-stu-id="fbc00-202">0</span></span>|  
|<span data-ttu-id="fbc00-203">ANATR</span><span class="sxs-lookup"><span data-stu-id="fbc00-203">ANATR</span></span>|<span data-ttu-id="fbc00-204">10308</span><span class="sxs-lookup"><span data-stu-id="fbc00-204">10308</span></span>|<span data-ttu-id="fbc00-205">1</span><span class="sxs-lookup"><span data-stu-id="fbc00-205">1</span></span>|  
|<span data-ttu-id="fbc00-206">ANATR</span><span class="sxs-lookup"><span data-stu-id="fbc00-206">ANATR</span></span>|<span data-ttu-id="fbc00-207">10625</span><span class="sxs-lookup"><span data-stu-id="fbc00-207">10625</span></span>|<span data-ttu-id="fbc00-208">1</span><span class="sxs-lookup"><span data-stu-id="fbc00-208">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbc00-209">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbc00-209">See also</span></span>

- [<span data-ttu-id="fbc00-210">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="fbc00-210">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="fbc00-211">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fbc00-211">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="fbc00-212">Úpravy dat přes DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="fbc00-212">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="fbc00-213">Více aktivních sad výsledků (MARS)</span><span class="sxs-lookup"><span data-stu-id="fbc00-213">Multiple Active Result Sets (MARS)</span></span>](./sql/multiple-active-result-sets-mars.md)
- [<span data-ttu-id="fbc00-214">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fbc00-214">ADO.NET Overview</span></span>](ado-net-overview.md)
