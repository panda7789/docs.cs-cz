---
title: Načítání dat pomocí čtečky dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 4370a7a700a01943548bf067827e6640245caf4e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516788"
---
# <a name="retrieving-data-using-a-datareader"></a><span data-ttu-id="b4cda-102">Načítání dat pomocí čtečky dat</span><span class="sxs-lookup"><span data-stu-id="b4cda-102">Retrieving Data Using a DataReader</span></span>
<span data-ttu-id="b4cda-103">Načítání dat pomocí **DataReader** zahrnuje vytvoření instance **příkaz** objektu a pak vytvořit **DataReader** voláním  **Command.ExecuteReader** načíst ze zdroje dat řádků.</span><span class="sxs-lookup"><span data-stu-id="b4cda-103">Retrieving data using a **DataReader** involves creating an instance of the **Command** object and then creating a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="b4cda-104">Následující příklad ukazuje použití **DataReader** kde `reader` představuje platné čtečky dat a `command` představuje objekt platný příkaz.</span><span class="sxs-lookup"><span data-stu-id="b4cda-104">The following example illustrates using a **DataReader** where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  
  
```  
reader = command.ExecuteReader();  
```  
  
 <span data-ttu-id="b4cda-105">Můžete použít **čtení** metodu **DataReader** objektu získat řádek ve výsledcích dotazu.</span><span class="sxs-lookup"><span data-stu-id="b4cda-105">You use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span> <span data-ttu-id="b4cda-106">Každý sloupec vrácený řádek se zpřístupní po předání název nebo Řadový odkaz na sloupec, který se **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="b4cda-106">You can access each column of the returned row by passing the name or ordinal reference of the column to the **DataReader**.</span></span> <span data-ttu-id="b4cda-107">Ale pro zajištění nejlepšího výkonu **DataReader** poskytuje řadu metod, které umožňují přístup k hodnot sloupce v jejich nativním datové typy (**GetDateTime**, **GetDouble**, **Getguid –**, **GetInt32**, a tak dále).</span><span class="sxs-lookup"><span data-stu-id="b4cda-107">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="b4cda-108">Seznam typu přístupové metody pro data specifickým pro zprostředkovatele **čtečky dat**, naleznete v tématu <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b4cda-108">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="b4cda-109">Pomocí metody typu přístupového objektu, za předpokladu, že příslušný datový typ je známo, snižuje počet při načítání hodnoty sloupce vyžaduje převod typů.</span><span class="sxs-lookup"><span data-stu-id="b4cda-109">Using the typed accessor methods, assuming the underlying data type is known, reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4cda-110">Windows Server 2003 verze rozhraní .NET Framework obsahuje další vlastnosti pro **DataReader**, **HasRows**, což vám umožní zjistit, jestli **DataReader**má nevrátil žádné výsledky před čtením z něj.</span><span class="sxs-lookup"><span data-stu-id="b4cda-110">The Windows Server 2003 release of the .NET Framework includes an additional property for the **DataReader**, **HasRows**, which enables you to determine if the **DataReader** has returned any results before reading from it.</span></span>  
  
 <span data-ttu-id="b4cda-111">Následující příklad Iteruje přes **DataReader** objekt a vrátí dva sloupce z každého řádku.</span><span class="sxs-lookup"><span data-stu-id="b4cda-111">The following code example iterates through a **DataReader** object, and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 <span data-ttu-id="b4cda-112">**DataReader** poskytuje bez vyrovnávací paměti datového proudu dat, která umožňuje procedurální logiku pro efektivní zpracování výsledků ze zdroje dat postupně.</span><span class="sxs-lookup"><span data-stu-id="b4cda-112">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="b4cda-113">**DataReader** je dobrou volbou při načítání velkých objemů dat, protože data neukládají do mezipaměti v paměti.</span><span class="sxs-lookup"><span data-stu-id="b4cda-113">The **DataReader** is a good choice when retrieving large amounts of data because the data is not cached in memory.</span></span>  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="b4cda-114">Zavření objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="b4cda-114">Closing the DataReader</span></span>  
 <span data-ttu-id="b4cda-115">Vždy byste měli zavolat **Zavřít** metoda po dokončení pomocí **DataReader** objektu.</span><span class="sxs-lookup"><span data-stu-id="b4cda-115">You should always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="b4cda-116">Pokud vaše **příkaz** obsahuje výstupní parametry nebo návratové hodnoty, nebudou k dispozici, dokud **DataReader** je zavřený.</span><span class="sxs-lookup"><span data-stu-id="b4cda-116">If your **Command** contains output parameters or return values, they will not be available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="b4cda-117">Všimněte si, že při **DataReader** je otevřený, **připojení** používá výhradně, který **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="b4cda-117">Note that while a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="b4cda-118">Nelze provést žádné příkazy pro **připojení**, včetně vytvoříte další **DataReader**, dokud původní **DataReader** je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="b4cda-118">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4cda-119">Nevolejte **Zavřít** nebo **Dispose** na **připojení**, **DataReader**, nebo jakýkoli jiný spravovaný objekt v **Finalize**  metoda vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="b4cda-119">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="b4cda-120">V finalizační metodu jenom uvolnění nespravovaných prostředků, které vaše třída vlastní přímo.</span><span class="sxs-lookup"><span data-stu-id="b4cda-120">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="b4cda-121">Pokud vaše třída není vlastníkem jakýchkoliv nespravovaných prostředků, nezahrnujte **Finalize** metoda v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="b4cda-121">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="b4cda-122">Další informace najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4cda-122">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="b4cda-123">Při načítání více sad výsledků dotazu pomocí NextResult</span><span class="sxs-lookup"><span data-stu-id="b4cda-123">Retrieving Multiple Result Sets using NextResult</span></span>  
 <span data-ttu-id="b4cda-124">Dojde k vrácení více sad výsledků dotazu **DataReader** poskytuje **NextResult** metoda procházením skrze výsledek nastaví v pořadí.</span><span class="sxs-lookup"><span data-stu-id="b4cda-124">If multiple result sets are returned, the **DataReader** provides the **NextResult** method to iterate through the result sets in order.</span></span> <span data-ttu-id="b4cda-125">Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků pomocí dvou příkazů SELECT <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b4cda-125">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="b4cda-126">Získávání informací o schématu z objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="b4cda-126">Getting Schema Information from the DataReader</span></span>  
 <span data-ttu-id="b4cda-127">Při **DataReader** je otevřít, můžete načíst informace o schématu o aktuální výsledek sada s použitím **GetSchemaTable** metoda.</span><span class="sxs-lookup"><span data-stu-id="b4cda-127">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="b4cda-128">**GetSchemaTable** vrátí <xref:System.Data.DataTable> objekt naplní řádky a sloupce, které obsahují informace o schématu pro aktuální sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="b4cda-128">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="b4cda-129">**DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="b4cda-129">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="b4cda-130">Každý sloupec řádku schématu tabulky se mapuje na vlastnost sloupec vrácený v výsledné sady, ve kterém **Názevsloupce** je název vlastnosti a hodnota sloupce je hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4cda-130">Each column of the schema table row maps to a property of the column returned in the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="b4cda-131">Následující příklad kódu zapíše informace o schématu pro **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="b4cda-131">The following code example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="b4cda-132">Práce s kapitol technologie OLE DB</span><span class="sxs-lookup"><span data-stu-id="b4cda-132">Working with OLE DB Chapters</span></span>  
 <span data-ttu-id="b4cda-133">Hierarchické sady řádků nebo kapitol (typ OLE DB **DBTYPE_HCHAPTER**, typ ADO **adChapter**) můžete získat pomocí <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b4cda-133">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**) can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="b4cda-134">Při dotazu, který zahrnuje kapitola se vrátí jako **DataReader**, kapitoly je vrácen jako sloupec, který **DataReader** a je přístupný jako **DataReader** objektu.</span><span class="sxs-lookup"><span data-stu-id="b4cda-134">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="b4cda-135">ADO.NET **datovou sadu** lze také použít k reprezentaci hierarchické sady řádků pomocí vztahů nadřazenosti a podřízenosti mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="b4cda-135">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets using parent-child relationships between tables.</span></span> <span data-ttu-id="b4cda-136">Další informace najdete v tématu [datové sady, datové tabulky a zobrazení dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4cda-136">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="b4cda-137">Následující příklad kódu používá zprostředkovatele MSDataShape ke generování objednávek pro každého zákazníka neočekávaný sloupec kapitoly v seznam zákazníků.</span><span class="sxs-lookup"><span data-stu-id="b4cda-137">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="b4cda-138">Vrací výsledky s soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="b4cda-138">Returning Results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="b4cda-139">Zprostředkovatel dat .NET Framework pro Oracle podporuje použití soubory Oracle REF CURSOR vrácení výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="b4cda-139">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="b4cda-140">Vrátí se Oracle REF CURSOR jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b4cda-140">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="b4cda-141">Můžete načíst **připojení OracleDataReader** objekt, který představuje objekt pro Oracle REF CURSOR pomocí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metoda a můžete také zadat <xref:System.Data.OracleClient.OracleCommand> , který vrací jeden nebo více soubory Oracle REF CURSOR jako  **Vlastnost SelectCommand** pro <xref:System.Data.OracleClient.OracleDataAdapter> použitou k vyplnění <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b4cda-141">You can retrieve an **OracleDataReader** object, that represents an Oracle REF CURSOR using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method, and you can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="b4cda-142">Pro přístup k REF CURSOR vrácená ze zdroje dat Oracle, vytvořte **OracleCommand** pro váš dotaz a přidejte výstupní parametr, který odkazuje kurzor REF **parametry** kolekce vaše  **OracleCommand**.</span><span class="sxs-lookup"><span data-stu-id="b4cda-142">To access a REF CURSOR returned from an Oracle data source, create an **OracleCommand** for your query and add an output parameter that references the REF CURSOR to the **Parameters** collection of your **OracleCommand**.</span></span> <span data-ttu-id="b4cda-143">Název parametru musí odpovídat názvu parametru REF CURSOR v dotazu.</span><span class="sxs-lookup"><span data-stu-id="b4cda-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="b4cda-144">Nastavit typ parametru **OracleType.Cursor**.</span><span class="sxs-lookup"><span data-stu-id="b4cda-144">Set the type of the parameter to **OracleType.Cursor**.</span></span> <span data-ttu-id="b4cda-145">**ExecuteReader** metodu vaše **OracleCommand** vrátí **připojení OracleDataReader** pro REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="b4cda-145">The **ExecuteReader** method of your **OracleCommand** will return an **OracleDataReader** for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="b4cda-146">Pokud vaše **OracleCommand** vrací více typů REF CURSOR, přidat více výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="b4cda-146">If your **OracleCommand** returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="b4cda-147">Dostanete různých typů REF CURSOR pomocí volání **OracleCommand.ExecuteReader** metody.</span><span class="sxs-lookup"><span data-stu-id="b4cda-147">You can access the different REF CURSORs by calling the **OracleCommand.ExecuteReader** method.</span></span> <span data-ttu-id="b4cda-148">Volání **ExecuteReader** vrátí **připojení OracleDataReader** odkazující na první REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="b4cda-148">The call to **ExecuteReader** returns an **OracleDataReader** referencing the first REF CURSOR.</span></span> <span data-ttu-id="b4cda-149">Potom můžete zavolat **OracleDataReader.NextResult** metody pro přístup k dalších typů REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="b4cda-149">You can then call the **OracleDataReader.NextResult** method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="b4cda-150">I když parametry v vaše **OracleCommand.Parameters** kolekce shoda REF CURSOR output parametry podle názvu, **připojení OracleDataReader** k nim přistupuje, aby byly přidány  **Parametry** kolekce.</span><span class="sxs-lookup"><span data-stu-id="b4cda-150">Although the parameters in your **OracleCommand.Parameters** collection match the REF CURSOR output parameters by name, the **OracleDataReader** accesses them in the order that they were added to the **Parameters** collection.</span></span>  
  
 <span data-ttu-id="b4cda-151">Představte si třeba následující balíček Oracle a tělo balíčku.</span><span class="sxs-lookup"><span data-stu-id="b4cda-151">For example, consider the following Oracle package and package body.</span></span>  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 <span data-ttu-id="b4cda-152">Následující kód vytvoří **OracleCommand** typů REF CURSOR z předchozí balíčku Oracle, který vrací tak, že přidáte dva parametry typu **OracleType.Cursor** k **parametry** kolekce.</span><span class="sxs-lookup"><span data-stu-id="b4cda-152">The following code creates an **OracleCommand** that returns the REF CURSORs from the previous Oracle package by adding two parameters of type **OracleType.Cursor** to the **Parameters** collection.</span></span>  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 <span data-ttu-id="b4cda-153">Následující kód vrátí výsledky z předchozího příkazu s **čtení** a **NextResult** metody **připojení OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="b4cda-153">The following code returns the results of the previous command using the **Read** and **NextResult** methods of the **OracleDataReader**.</span></span> <span data-ttu-id="b4cda-154">Parametry REF CURSOR jsou vráceny v pořadí.</span><span class="sxs-lookup"><span data-stu-id="b4cda-154">The REF CURSOR parameters are returned in order.</span></span>  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 <span data-ttu-id="b4cda-155">Následující příklad používá k naplnění předchozí příkaz **datovou sadu** s výsledky balíčku Oracle.</span><span class="sxs-lookup"><span data-stu-id="b4cda-155">The following example uses the previous command to populate a **DataSet** with the results of the Oracle package.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4cda-156">Aby se zabránilo **OverFlowException –**, doporučujeme také zpracovat jakýkoli převod z typu Oracle číslo na platný typ rozhraní .NET Framework před uložením hodnoty v **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="b4cda-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a **DataRow**.</span></span> <span data-ttu-id="b4cda-157">Můžete použít **FillError** událostí k určení, zda **OverFlowException –** došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="b4cda-157">You can use the **FillError** event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="b4cda-158">Další informace o **FillError** událostí, naleznete v tématu [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="b4cda-158">For more information on the **FillError** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4cda-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4cda-159">See Also</span></span>  
 [<span data-ttu-id="b4cda-160">Práce s čtečky dat</span><span class="sxs-lookup"><span data-stu-id="b4cda-160">Working with DataReaders</span></span>](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="b4cda-161">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="b4cda-161">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="b4cda-162">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="b4cda-162">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="b4cda-163">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="b4cda-163">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="b4cda-164">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b4cda-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
