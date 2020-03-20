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
# <a name="populating-a-dataset-from-a-dataadapter"></a><span data-ttu-id="208cf-102">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="208cf-102">Populating a DataSet from a DataAdapter</span></span>
<span data-ttu-id="208cf-103">ADO.NET <xref:System.Data.DataSet> je rezidentní reprezentace dat rezidentní v paměti, která poskytuje konzistentní relační programovací model nezávislý na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="208cf-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model independent of the data source.</span></span> <span data-ttu-id="208cf-104">Představuje `DataSet` úplnou sadu dat, která obsahuje tabulky, omezení a relace mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="208cf-104">The `DataSet` represents a complete set of data that includes tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="208cf-105">Vzhledem `DataSet` k tomu, že `DataSet` je nezávislý na zdroji dat, může obsahovat data místní do aplikace a data z více zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="208cf-105">Because the `DataSet` is independent of the data source, a `DataSet` can include data local to the application, and data from multiple data sources.</span></span> <span data-ttu-id="208cf-106">Interakce se stávajícími zdroji `DataAdapter`dat je řízena prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="208cf-106">Interaction with existing data sources is controlled through the `DataAdapter`.</span></span>  
  
 <span data-ttu-id="208cf-107">Vlastnost `SelectCommand` `DataAdapter` je `Command` objekt, který načítá data ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="208cf-107">The `SelectCommand` property of the `DataAdapter` is a `Command` object that retrieves data from the data source.</span></span> <span data-ttu-id="208cf-108">`InsertCommand`Vlastnosti `UpdateCommand`, `DeleteCommand` a `DataAdapter` jsou `Command` objekty, které spravují aktualizace dat ve zdroji dat podle `DataSet`změn provedených v datech v .</span><span class="sxs-lookup"><span data-stu-id="208cf-108">The `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of the `DataAdapter` are `Command` objects that manage updates to the data in the data source according to modifications made to the data in the `DataSet`.</span></span> <span data-ttu-id="208cf-109">Tyto vlastnosti jsou podrobněji popsány v [aktualizaci zdrojů dat pomocí datových adaptérů](updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="208cf-109">These properties are covered in more detail in [Updating Data Sources with DataAdapters](updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="208cf-110">Metoda `Fill` `DataAdapter` se používá k naplnění `DataSet` s výsledky `SelectCommand` . `DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="208cf-110">The `Fill` method of the `DataAdapter` is used to populate a `DataSet` with the results of the `SelectCommand` of the `DataAdapter`.</span></span> <span data-ttu-id="208cf-111">`Fill`bere jako jeho `DataSet` argumenty a, které `DataTable` mají být naplněny `DataTable` a objekt nebo název, `SelectCommand`který má být vyplněn řádky vrácenými z .</span><span class="sxs-lookup"><span data-stu-id="208cf-111">`Fill` takes as its arguments a `DataSet` to be populated, and a `DataTable` object, or the name of the `DataTable` to be filled with the rows returned from the `SelectCommand`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="208cf-112">Použití `DataAdapter` načíst všechny tabulky nějakou dobu trvá, zejména v případě, že existuje mnoho řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="208cf-112">Using the `DataAdapter` to retrieve all of a table takes time, especially if there are many rows in the table.</span></span> <span data-ttu-id="208cf-113">Důvodem je, že přístup k databázi, vyhledání a zpracování dat a potom přenos dat do klienta je časově náročné.</span><span class="sxs-lookup"><span data-stu-id="208cf-113">This is because accessing the database, locating and processing the data, and then transferring the data to the client is time-consuming.</span></span> <span data-ttu-id="208cf-114">Vytažení matné tabulky klientovi také uzamkne všechny řádky na serveru.</span><span class="sxs-lookup"><span data-stu-id="208cf-114">Pulling all of the table to the client also locks all of the rows on the server.</span></span> <span data-ttu-id="208cf-115">Chcete-li zlepšit výkon, `WHERE` můžete použít klauzuli výrazně snížit počet řádků vrácených klientovi.</span><span class="sxs-lookup"><span data-stu-id="208cf-115">To improve performance, you can use the `WHERE` clause to greatly reduce the number of rows returned to the client.</span></span> <span data-ttu-id="208cf-116">Můžete také snížit množství dat vrácených klientovi pouze explicitně `SELECT` výpis požadované sloupce v příkazu.</span><span class="sxs-lookup"><span data-stu-id="208cf-116">You can also reduce the amount of data returned to the client by only explicitly listing required columns in the `SELECT` statement.</span></span> <span data-ttu-id="208cf-117">Dalším dobrým řešením je načíst řádky v dávkách (například několik set řádků najednou) a pouze načíst další dávku po dokončení klienta s aktuální dávkou.</span><span class="sxs-lookup"><span data-stu-id="208cf-117">Another good workaround is to retrieve the rows in batches (such as several hundred rows at a time) and only retrieve the next batch when the client is finished with the current batch.</span></span>  
  
 <span data-ttu-id="208cf-118">Metoda `Fill` používá `DataReader` objekt implicitně vrátit názvy sloupců a typy, které `DataSet`se používají k vytvoření tabulek v `DataSet`, a data k naplnění řádků tabulek v .</span><span class="sxs-lookup"><span data-stu-id="208cf-118">The `Fill` method uses the `DataReader` object implicitly to return the column names and types that are used to create the tables in the `DataSet`, and the data to populate the rows of the tables in the `DataSet`.</span></span> <span data-ttu-id="208cf-119">Tabulky a sloupce jsou vytvořeny pouze v případě, že ještě neexistují. v `Fill` opačném `DataSet` případě použije existující schéma.</span><span class="sxs-lookup"><span data-stu-id="208cf-119">Tables and columns are only created if they do not already exist; otherwise `Fill` uses the existing `DataSet` schema.</span></span> <span data-ttu-id="208cf-120">Typy sloupců jsou vytvářeny jako typy rozhraní .NET Framework podle tabulek v [části Mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="208cf-120">Column types are created as .NET Framework types according to the tables in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span> <span data-ttu-id="208cf-121">Primární klíče nejsou vytvořeny, pokud neexistují `DataAdapter`ve zdroji dat a **.**`MissingSchemaAction`</span><span class="sxs-lookup"><span data-stu-id="208cf-121">Primary keys are not created unless they exist in the data source and `DataAdapter`**.**`MissingSchemaAction`</span></span> <span data-ttu-id="208cf-122">je nastavena na `MissingSchemaAction` **.** `AddWithKey`.</span><span class="sxs-lookup"><span data-stu-id="208cf-122">is set to `MissingSchemaAction`**.**`AddWithKey`.</span></span> <span data-ttu-id="208cf-123">Pokud `Fill` zjistí, že pro tabulku existuje primární klíč, přepíše data v souboru `DataSet` s daty ze zdroje dat pro řádky, kde hodnoty sloupce primárního klíče odpovídají hodnotám řádku vráceného ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="208cf-123">If `Fill` finds that a primary key exists for a table, it will overwrite data in the `DataSet` with data from the data source for rows where the primary key column values match those of the row returned from the data source.</span></span> <span data-ttu-id="208cf-124">Pokud není nalezen žádný primární klíč, data jsou `DataSet`připojena k tabulkám v .</span><span class="sxs-lookup"><span data-stu-id="208cf-124">If no primary key is found, the data is appended to the tables in the `DataSet`.</span></span> <span data-ttu-id="208cf-125">`Fill`používá všechna mapování, která mohou `DataSet` existovat při naplnění (viz [DataAdapter DataTable a DataColumn Mappings).](dataadapter-datatable-and-datacolumn-mappings.md)</span><span class="sxs-lookup"><span data-stu-id="208cf-125">`Fill` uses any mappings that may exist when you populate the `DataSet` (see [DataAdapter DataTable and DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="208cf-126">Pokud `SelectCommand` vrátí výsledky OUTER JOIN, `DataAdapter` nenastaví `PrimaryKey` hodnotu pro `DataTable`výsledné .</span><span class="sxs-lookup"><span data-stu-id="208cf-126">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` does not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="208cf-127">Musíte definovat `PrimaryKey` sami, abyste se ujistili, že duplicitní řádky jsou vyřešeny správně.</span><span class="sxs-lookup"><span data-stu-id="208cf-127">You must define the `PrimaryKey` yourself to make sure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="208cf-128">Další informace naleznete [v tématu Definování primárních klíčů](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="208cf-128">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="208cf-129">Následující příklad kódu vytvoří <xref:System.Data.SqlClient.SqlDataAdapter> instanci, <xref:System.Data.SqlClient.SqlConnection> která používá `Northwind` databázi serveru <xref:System.Data.DataTable> Microsoft `DataSet` SQL Server a naplní seznam zákazníků v a.</span><span class="sxs-lookup"><span data-stu-id="208cf-129">The following code example creates an instance of a <xref:System.Data.SqlClient.SqlDataAdapter> that uses a <xref:System.Data.SqlClient.SqlConnection> to the Microsoft SQL Server `Northwind` database and populates a <xref:System.Data.DataTable> in a `DataSet` with the list of customers.</span></span> <span data-ttu-id="208cf-130">Příkaz SQL <xref:System.Data.SqlClient.SqlConnection> a argumenty <xref:System.Data.SqlClient.SqlDataAdapter> předané konstruktoru <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> se používají <xref:System.Data.SqlClient.SqlDataAdapter>k vytvoření vlastnosti .</span><span class="sxs-lookup"><span data-stu-id="208cf-130">The SQL statement and <xref:System.Data.SqlClient.SqlConnection> arguments passed to the <xref:System.Data.SqlClient.SqlDataAdapter> constructor are used to create the <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> property of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="208cf-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="208cf-131">Example</span></span>  
  
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
> <span data-ttu-id="208cf-132">Kód zobrazený v tomto příkladu explicitně neotevře a nezavře . `Connection`</span><span class="sxs-lookup"><span data-stu-id="208cf-132">The code shown in this example does not explicitly open and close the `Connection`.</span></span> <span data-ttu-id="208cf-133">Metoda `Fill` implicitně `Connection` otevře, `DataAdapter` že používá, pokud zjistí, že připojení již není otevřen.</span><span class="sxs-lookup"><span data-stu-id="208cf-133">The `Fill` method implicitly opens the `Connection` that the `DataAdapter` is using if it finds that the connection is not already open.</span></span> <span data-ttu-id="208cf-134">Pokud `Fill` se připojení otevře, zavře připojení `Fill` také po dokončení.</span><span class="sxs-lookup"><span data-stu-id="208cf-134">If `Fill` opened the connection, it also closes the connection when `Fill` is finished.</span></span> <span data-ttu-id="208cf-135">To může zjednodušit kód při zpracování jedné `Fill` operace, `Update`jako je například nebo .</span><span class="sxs-lookup"><span data-stu-id="208cf-135">This can simplify your code when you deal with a single operation such as a `Fill` or an `Update`.</span></span> <span data-ttu-id="208cf-136">Pokud však provádíte více operací, které vyžadují otevřené připojení, můžete zlepšit výkon `Open` aplikace `Connection`explicitním voláním metody , provedením operací `Close` proti `Connection`zdroji dat a voláním metody .</span><span class="sxs-lookup"><span data-stu-id="208cf-136">However, if you are performing multiple operations that require an open connection, you can improve the performance of your application by explicitly calling the `Open` method of the `Connection`, performing the operations against the data source, and then calling the `Close` method of the `Connection`.</span></span> <span data-ttu-id="208cf-137">Měli byste se pokusit zachovat připojení ke zdroji dat otevřené co nejdříve uvolnit prostředky pro použití jinými klientskými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="208cf-137">You should try to keep connections to the data source open as briefly as possible to free resources for use by other client applications.</span></span>  
  
## <a name="multiple-result-sets"></a><span data-ttu-id="208cf-138">Více sad výsledků</span><span class="sxs-lookup"><span data-stu-id="208cf-138">Multiple Result Sets</span></span>  
 <span data-ttu-id="208cf-139">Pokud `DataAdapter` dojde k více sad výsledků, vytvoří `DataSet`více tabulek v .</span><span class="sxs-lookup"><span data-stu-id="208cf-139">If the `DataAdapter` encounters multiple result sets, it creates multiple tables in the `DataSet`.</span></span> <span data-ttu-id="208cf-140">Tabulky mají přírůstkový výchozí název tabulky*N*, počínaje "Tabulka" pro table0.</span><span class="sxs-lookup"><span data-stu-id="208cf-140">The tables are given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span> <span data-ttu-id="208cf-141">Pokud je název tabulky předán `Fill` metodě jako argument, jsou tabulkám přidělen přírůstkový výchozí název TableName*N*, počínaje názvem TableName pro TableName0.</span><span class="sxs-lookup"><span data-stu-id="208cf-141">If a table name is passed as an argument to the `Fill` method, the tables are given an incremental default name of TableName*N*, starting with "TableName" for TableName0.</span></span>  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a><span data-ttu-id="208cf-142">Naplnění datové sady z více datových adaptérů</span><span class="sxs-lookup"><span data-stu-id="208cf-142">Populating a DataSet from Multiple DataAdapters</span></span>  
 <span data-ttu-id="208cf-143">`DataAdapter` S `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="208cf-143">Any number of `DataAdapter` objects can be used with a `DataSet`.</span></span> <span data-ttu-id="208cf-144">Každý `DataAdapter` z nich lze použít `DataTable` k vyplnění jednoho nebo více objektů a vyřešit aktualizace zpět do příslušného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="208cf-144">Each `DataAdapter` can be used to fill one or more `DataTable` objects and resolve updates back to the relevant data source.</span></span> <span data-ttu-id="208cf-145">`DataRelation`a `Constraint` objekty mohou `DataSet` být přidány místně, což umožňuje propojit data z odlišných zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="208cf-145">`DataRelation` and `Constraint` objects can be added to the `DataSet` locally, which enables you to relate data from dissimilar data sources.</span></span> <span data-ttu-id="208cf-146">Může `DataSet` například obsahovat data z databáze serveru Microsoft SQL Server, databáze IBM DB2 vystavené prostřednictvím technologie OLE DB a zdroje dat, který streamuje xml.</span><span class="sxs-lookup"><span data-stu-id="208cf-146">For example, a `DataSet` can contain data from a Microsoft SQL Server database, an IBM DB2 database exposed through OLE DB, and a data source that streams XML.</span></span> <span data-ttu-id="208cf-147">Jeden nebo `DataAdapter` více objektů může zpracovávat komunikaci s každým zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="208cf-147">One or more `DataAdapter` objects can handle communication to each data source.</span></span>  
  
### <a name="example"></a><span data-ttu-id="208cf-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="208cf-148">Example</span></span>  
 <span data-ttu-id="208cf-149">Následující příklad kódu naplní seznam zákazníků `Northwind` z databáze na serveru Microsoft SQL `Northwind` Server a seznam objednávek z databáze uložené v aplikaci Microsoft Access 2000.</span><span class="sxs-lookup"><span data-stu-id="208cf-149">The following code example populates a list of customers from the `Northwind` database on Microsoft SQL Server, and a list of orders from the `Northwind` database stored in Microsoft Access 2000.</span></span> <span data-ttu-id="208cf-150">Vyplněné tabulky souvisejí `DataRelation`s a a seznam zákazníků se pak zobrazí s objednávkami pro tohoto zákazníka.</span><span class="sxs-lookup"><span data-stu-id="208cf-150">The filled tables are related with a `DataRelation`, and the list of customers is then displayed with the orders for that customer.</span></span> <span data-ttu-id="208cf-151">Další informace `DataRelation` o objektech naleznete v [tématech Přidání datových vztahů](./dataset-datatable-dataview/adding-datarelations.md) a [Navigace datových vztahů](./dataset-datatable-dataview/navigating-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="208cf-151">For more information about `DataRelation` objects, see [Adding DataRelations](./dataset-datatable-dataview/adding-datarelations.md) and [Navigating DataRelations](./dataset-datatable-dataview/navigating-datarelations.md).</span></span>  
  
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
  
## <a name="sql-server-decimal-type"></a><span data-ttu-id="208cf-152">Desítkový typ serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="208cf-152">SQL Server Decimal Type</span></span>  
 <span data-ttu-id="208cf-153">Ve výchozím `DataSet` nastavení ukládá data pomocí datových typů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="208cf-153">By default, the `DataSet` stores data by using .NET Framework data types.</span></span> <span data-ttu-id="208cf-154">Pro většinu aplikací poskytují pohodlné znázornění informací o zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="208cf-154">For most applications, these provide a convenient representation of data source information.</span></span> <span data-ttu-id="208cf-155">Tato reprezentace však může způsobit problém, pokud je datový typ ve zdroji dat desítkový nebo číselný datový typ serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="208cf-155">However, this representation may cause a problem when the data type in the data source is a SQL Server decimal or numeric data type.</span></span> <span data-ttu-id="208cf-156">Datový typ `decimal` rozhraní .NET Framework umožňuje maximálně 28 platných `decimal` číslic, zatímco datový typ serveru SQL Server umožňuje 38 platných číslic.</span><span class="sxs-lookup"><span data-stu-id="208cf-156">The .NET Framework `decimal` data type allows a maximum of 28 significant digits, whereas the SQL Server `decimal` data type allows 38 significant digits.</span></span> <span data-ttu-id="208cf-157">Pokud `SqlDataAdapter` během `Fill` operace určí, že přesnost pole `decimal` serveru SQL Server je větší než 28 `DataTable`znaků, aktuální řádek není přidán do .</span><span class="sxs-lookup"><span data-stu-id="208cf-157">If the `SqlDataAdapter` determines during a `Fill` operation that the precision of a SQL Server `decimal` field is larger than 28 characters, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="208cf-158">Místo `FillError` toho dojde k události, která umožňuje určit, zda dojde ke ztrátě přesnosti a odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="208cf-158">Instead the `FillError` event occurs, which enables you to determine whether a loss of precision will occur, and respond appropriately.</span></span> <span data-ttu-id="208cf-159">Další informace o `FillError` události naleznete v tématu [Zpracování událostí datového adaptéru](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="208cf-159">For more information about the `FillError` event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span> <span data-ttu-id="208cf-160">Chcete-li získat `decimal` hodnotu serveru SQL <xref:System.Data.SqlClient.SqlDataReader> Server, <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> můžete také použít objekt a volat metodu.</span><span class="sxs-lookup"><span data-stu-id="208cf-160">To get the SQL Server `decimal` value, you can also use a <xref:System.Data.SqlClient.SqlDataReader> object and call the <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> method.</span></span>  
  
 <span data-ttu-id="208cf-161">ADO.NET 2.0 zavedla zvýšenou podporu <xref:System.Data.SqlTypes> v . `DataSet`</span><span class="sxs-lookup"><span data-stu-id="208cf-161">ADO.NET 2.0 introduced enhanced support for <xref:System.Data.SqlTypes> in the `DataSet`.</span></span> <span data-ttu-id="208cf-162">Další informace naleznete [v tématu SqlTypes a DataSet](./sql/sqltypes-and-the-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="208cf-162">For more information, see [SqlTypes and the DataSet](./sql/sqltypes-and-the-dataset.md).</span></span>  
  
## <a name="ole-db-chapters"></a><span data-ttu-id="208cf-163">Kapitoly OLE DB</span><span class="sxs-lookup"><span data-stu-id="208cf-163">OLE DB Chapters</span></span>  
 <span data-ttu-id="208cf-164">Hierarchické sady řádků nebo kapitoly (typ `DBTYPE_HCHAPTER`OLE `adChapter`DB , typ ADO) `DataSet`lze použít k vyplnění obsahu .</span><span class="sxs-lookup"><span data-stu-id="208cf-164">Hierarchical rowsets, or chapters (OLE DB type `DBTYPE_HCHAPTER`, ADO type `adChapter`) can be used to fill the contents of a `DataSet`.</span></span> <span data-ttu-id="208cf-165">Když <xref:System.Data.OleDb.OleDbDataAdapter> se během operace setká `Fill` se sloupcem s kapitolou, `DataTable` vytvoří se pro sloupec s kapitolami a tato tabulka je vyplněna sloupci a řádky z kapitoly.</span><span class="sxs-lookup"><span data-stu-id="208cf-165">When the <xref:System.Data.OleDb.OleDbDataAdapter> encounters a chaptered column during a `Fill` operation, a `DataTable` is created for the chaptered column, and that table is filled with the columns and rows from the chapter.</span></span> <span data-ttu-id="208cf-166">Tabulka vytvořená pro sloupec s kapitolami je pojmenována pomocí názvu nadřazené tabulky i názvu sloupce s kapitolami ve formuláři*ParentTableNameChapteredColumnName*.</span><span class="sxs-lookup"><span data-stu-id="208cf-166">The table created for the chaptered column is named by using both the parent table name and the chaptered column name in the form "*ParentTableNameChapteredColumnName*".</span></span> <span data-ttu-id="208cf-167">Pokud tabulka již existuje `DataSet` v tabulce, která odpovídá názvu sloupce s kapitolou, je aktuální tabulka vyplněna daty kapitoly.</span><span class="sxs-lookup"><span data-stu-id="208cf-167">If a table already exists in the `DataSet` that matches the name of the chaptered column, the current table is filled with the chapter data.</span></span> <span data-ttu-id="208cf-168">Pokud v existující tabulce není žádný sloupec, který by odpovídal sloupci nalezenému v kapitole, je přidán nový sloupec.</span><span class="sxs-lookup"><span data-stu-id="208cf-168">If there is no column in an existing table that matches a column found in the chapter, a new column is added.</span></span>  
  
 <span data-ttu-id="208cf-169">Před tím, `DataSet` než jsou tabulky v tabulce vyplněny daty ve sloupcích s kapitolami, je vytvořen vztah mezi nadřazenou a podřízenou tabulkou hierarchické sady `DataRelation` řádků přidáním celočíselného sloupce do nadřazené i podřízené tabulky, nastavením nadřazeného sloupce na automatický přírůstek a vytvořením přidaných sloupců z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="208cf-169">Before the tables in the `DataSet` are filled with the data in the chaptered columns, a relation is created between the parent and child tables of the hierarchical rowset by adding an integer column to both the parent and child table, setting the parent column to auto-increment, and creating a `DataRelation` using the added columns from both tables.</span></span> <span data-ttu-id="208cf-170">Přidaná relační vazba je pojmenována pomocí názvů nadřazených tabulek a sloupců kapitol ve formuláři*ParentTableNameChapterColumnName.*</span><span class="sxs-lookup"><span data-stu-id="208cf-170">The added relation is named by using the parent table and chapter column names in the form "*ParentTableNameChapterColumnName*".</span></span>  
  
 <span data-ttu-id="208cf-171">Všimněte si, že související `DataSet`sloupec existuje pouze v .</span><span class="sxs-lookup"><span data-stu-id="208cf-171">Note that the related column only exists in the `DataSet`.</span></span> <span data-ttu-id="208cf-172">Následné výplně ze zdroje dat mohou způsobit přidání nových řádků do tabulek namísto slučování změn do existujících řádků.</span><span class="sxs-lookup"><span data-stu-id="208cf-172">Subsequent fills from the data source can cause new rows to be added to the tables instead of changes being merged into existing rows.</span></span>  
  
 <span data-ttu-id="208cf-173">Všimněte si také, `DataAdapter.Fill` že pokud `DataTable`použijete přetížení, které trvá , bude vyplněna pouze tato tabulka.</span><span class="sxs-lookup"><span data-stu-id="208cf-173">Note also that, if you use the `DataAdapter.Fill` overload that takes a `DataTable`, only that table will be filled.</span></span> <span data-ttu-id="208cf-174">Do tabulky bude stále přidán sloupec s automatickým přírůstkem celéčíslo, ale nebude vytvořena ani vyplněna žádná podřízená tabulka a nebude vytvořen žádný vztah.</span><span class="sxs-lookup"><span data-stu-id="208cf-174">An auto-incrementing integer column will still be added to the table, but no child table will be created or filled, and no relation will be created.</span></span>  
  
 <span data-ttu-id="208cf-175">Následující příklad používá zprostředkovatele MSDataShape ke generování sloupce kapitol objednávek pro každého zákazníka v seznamu zákazníků.</span><span class="sxs-lookup"><span data-stu-id="208cf-175">The following example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span> <span data-ttu-id="208cf-176">A `DataSet` je pak vyplněna daty.</span><span class="sxs-lookup"><span data-stu-id="208cf-176">A `DataSet` is then filled with the data.</span></span>  
  
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
  
 <span data-ttu-id="208cf-177">Po `Fill` dokončení `DataSet` operace obsahuje dvě tabulky: `Customers` a `CustomersOrders`, kde `CustomersOrders` představuje sloupec s kapitolou.</span><span class="sxs-lookup"><span data-stu-id="208cf-177">When the `Fill` operation is complete, the `DataSet` contains two tables: `Customers` and `CustomersOrders`, where `CustomersOrders` represents the chaptered column.</span></span> <span data-ttu-id="208cf-178">`Orders` Do `Customers` tabulky je přidán další sloupec s názvem `CustomersOrders` a do `CustomersOrders` tabulky je přidán další pojmenovaný sloupec.</span><span class="sxs-lookup"><span data-stu-id="208cf-178">An additional column named `Orders` is added to the `Customers` table, and an additional column named `CustomersOrders` is added to the `CustomersOrders` table.</span></span> <span data-ttu-id="208cf-179">Sloupec `Orders` v `Customers` tabulce je nastaven na automatický přírůstek.</span><span class="sxs-lookup"><span data-stu-id="208cf-179">The `Orders` column in the `Customers` table is set to auto-increment.</span></span> <span data-ttu-id="208cf-180">A `DataRelation` `CustomersOrders`, je vytvořen pomocí sloupců, které `Customers` byly přidány do tabulek s jako nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="208cf-180">A `DataRelation`, `CustomersOrders`, is created by using the columns that were added to the tables with `Customers` as the parent table.</span></span> <span data-ttu-id="208cf-181">V následujících tabulkách jsou uvedeny některé ukázkové výsledky.</span><span class="sxs-lookup"><span data-stu-id="208cf-181">The following tables show some sample results.</span></span>  
  
### <a name="tablename-customers"></a><span data-ttu-id="208cf-182">Název_tabulky: Zákazníci</span><span class="sxs-lookup"><span data-stu-id="208cf-182">TableName: Customers</span></span>  
  
|<span data-ttu-id="208cf-183">CustomerID</span><span class="sxs-lookup"><span data-stu-id="208cf-183">CustomerID</span></span>|<span data-ttu-id="208cf-184">CompanyName</span><span class="sxs-lookup"><span data-stu-id="208cf-184">CompanyName</span></span>|<span data-ttu-id="208cf-185">Orders</span><span class="sxs-lookup"><span data-stu-id="208cf-185">Orders</span></span>|  
|----------------|-----------------|------------|  
|<span data-ttu-id="208cf-186">ALFKI</span><span class="sxs-lookup"><span data-stu-id="208cf-186">ALFKI</span></span>|<span data-ttu-id="208cf-187">Alfreds Futterkiste</span><span class="sxs-lookup"><span data-stu-id="208cf-187">Alfreds Futterkiste</span></span>|<span data-ttu-id="208cf-188">0</span><span class="sxs-lookup"><span data-stu-id="208cf-188">0</span></span>|  
|<span data-ttu-id="208cf-189">ANATR</span><span class="sxs-lookup"><span data-stu-id="208cf-189">ANATR</span></span>|<span data-ttu-id="208cf-190">Ana Trujillo Emparedados y helados</span><span class="sxs-lookup"><span data-stu-id="208cf-190">Ana Trujillo Emparedados y helados</span></span>|<span data-ttu-id="208cf-191">1</span><span class="sxs-lookup"><span data-stu-id="208cf-191">1</span></span>|  
  
### <a name="tablename-customersorders"></a><span data-ttu-id="208cf-192">Název_tabulky: Objednávky zákazníků</span><span class="sxs-lookup"><span data-stu-id="208cf-192">TableName: CustomersOrders</span></span>  
  
|<span data-ttu-id="208cf-193">CustomerID</span><span class="sxs-lookup"><span data-stu-id="208cf-193">CustomerID</span></span>|<span data-ttu-id="208cf-194">OrderID</span><span class="sxs-lookup"><span data-stu-id="208cf-194">OrderID</span></span>|<span data-ttu-id="208cf-195">Objednávky zákazníků</span><span class="sxs-lookup"><span data-stu-id="208cf-195">CustomersOrders</span></span>|  
|----------------|-------------|---------------------|  
|<span data-ttu-id="208cf-196">ALFKI</span><span class="sxs-lookup"><span data-stu-id="208cf-196">ALFKI</span></span>|<span data-ttu-id="208cf-197">10643</span><span class="sxs-lookup"><span data-stu-id="208cf-197">10643</span></span>|<span data-ttu-id="208cf-198">0</span><span class="sxs-lookup"><span data-stu-id="208cf-198">0</span></span>|  
|<span data-ttu-id="208cf-199">ALFKI</span><span class="sxs-lookup"><span data-stu-id="208cf-199">ALFKI</span></span>|<span data-ttu-id="208cf-200">10692</span><span class="sxs-lookup"><span data-stu-id="208cf-200">10692</span></span>|<span data-ttu-id="208cf-201">0</span><span class="sxs-lookup"><span data-stu-id="208cf-201">0</span></span>|  
|<span data-ttu-id="208cf-202">ANATR</span><span class="sxs-lookup"><span data-stu-id="208cf-202">ANATR</span></span>|<span data-ttu-id="208cf-203">10308</span><span class="sxs-lookup"><span data-stu-id="208cf-203">10308</span></span>|<span data-ttu-id="208cf-204">1</span><span class="sxs-lookup"><span data-stu-id="208cf-204">1</span></span>|  
|<span data-ttu-id="208cf-205">ANATR</span><span class="sxs-lookup"><span data-stu-id="208cf-205">ANATR</span></span>|<span data-ttu-id="208cf-206">10625</span><span class="sxs-lookup"><span data-stu-id="208cf-206">10625</span></span>|<span data-ttu-id="208cf-207">1</span><span class="sxs-lookup"><span data-stu-id="208cf-207">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="208cf-208">Viz také</span><span class="sxs-lookup"><span data-stu-id="208cf-208">See also</span></span>

- [<span data-ttu-id="208cf-209">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="208cf-209">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="208cf-210">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="208cf-210">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="208cf-211">Úpravy dat přes DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="208cf-211">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="208cf-212">Více aktivních sad výsledků (MARS)</span><span class="sxs-lookup"><span data-stu-id="208cf-212">Multiple Active Result Sets (MARS)</span></span>](./sql/multiple-active-result-sets-mars.md)
- [<span data-ttu-id="208cf-213">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="208cf-213">ADO.NET Overview</span></span>](ado-net-overview.md)
