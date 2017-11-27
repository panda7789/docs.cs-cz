---
title: "Načítání dat pomocí DataReader –"
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
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0b66ca2fbcc760598b771b4c02a46acc3c9c1d4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-data-using-a-datareader"></a><span data-ttu-id="646ab-102">Načítání dat pomocí DataReader –</span><span class="sxs-lookup"><span data-stu-id="646ab-102">Retrieving Data Using a DataReader</span></span>
<span data-ttu-id="646ab-103">Načítání dat pomocí **DataReader –** zahrnuje vytvoření instance **příkaz** objektu a pak vytvořit **DataReader –** voláním  **Command.ExecuteReader** k načtení řádků ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="646ab-103">Retrieving data using a **DataReader** involves creating an instance of the **Command** object and then creating a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="646ab-104">Následující příklad ilustruje, použití **DataReader –** kde `reader` představuje platnou DataReader – a `command` představuje platný objekt příkazu.</span><span class="sxs-lookup"><span data-stu-id="646ab-104">The following example illustrates using a **DataReader** where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  
  
```  
reader = command.ExecuteReader();  
```  
  
 <span data-ttu-id="646ab-105">Můžete použít **čtení** metodu **DataReader –** objekt, který chcete získat řádek z výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="646ab-105">You use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span> <span data-ttu-id="646ab-106">Každý sloupec vrácený řádek dostanete předáním odkazu na pořadí sloupce, který se na název **DataReader –**.</span><span class="sxs-lookup"><span data-stu-id="646ab-106">You can access each column of the returned row by passing the name or ordinal reference of the column to the **DataReader**.</span></span> <span data-ttu-id="646ab-107">Pro nejlepší výkon, ale **DataReader –** poskytuje řadu metod, které vám umožní přístup k hodnot sloupce v jeho nativní datové typy (**GetDateTime**, **GetDouble**, **Getguid –**, **GetInt32**a tak dále).</span><span class="sxs-lookup"><span data-stu-id="646ab-107">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="646ab-108">Seznam typové přístupových metod pro data specifický pro zprostředkovatele **DataReaders**, najdete v části <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="646ab-108">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="646ab-109">Pomocí zadaných přístupových metod, za předpokladu, že se označuje základní datový typ, snižuje množství při načítání hodnoty sloupce vyžaduje převod typů.</span><span class="sxs-lookup"><span data-stu-id="646ab-109">Using the typed accessor methods, assuming the underlying data type is known, reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="646ab-110">Zahrnuje další vlastnost pro Windows Server 2003 verze rozhraní .NET Framework **DataReader –**, **HasRows**, což umožňuje zjistit, jestli **DataReader –**má nevrátil žádné výsledky před čtení z něj.</span><span class="sxs-lookup"><span data-stu-id="646ab-110">The Windows Server 2003 release of the .NET Framework includes an additional property for the **DataReader**, **HasRows**, which enables you to determine if the **DataReader** has returned any results before reading from it.</span></span>  
  
 <span data-ttu-id="646ab-111">Následující příklad kódu iteruje **DataReader** objekt a vrátí dva sloupce z každého řádku.</span><span class="sxs-lookup"><span data-stu-id="646ab-111">The following code example iterates through a **DataReader** object, and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 <span data-ttu-id="646ab-112">**DataReader** poskytuje bez vyrovnávací paměti datový proud dat, která umožňuje procedurální logiku a efektivní zpracování výsledků ze zdroje dat postupně.</span><span class="sxs-lookup"><span data-stu-id="646ab-112">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="646ab-113">**DataReader** je vhodné použít při načítání velkých objemů dat, protože není uložen v mezipaměti v paměti.</span><span class="sxs-lookup"><span data-stu-id="646ab-113">The **DataReader** is a good choice when retrieving large amounts of data because the data is not cached in memory.</span></span>  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="646ab-114">Zavření objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="646ab-114">Closing the DataReader</span></span>  
 <span data-ttu-id="646ab-115">Vždy byste měli zavolat **Zavřít** metoda po dokončení pomocí **DataReader** objektu.</span><span class="sxs-lookup"><span data-stu-id="646ab-115">You should always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="646ab-116">Pokud vaše **příkaz** výstup obsahuje parametry nebo návratové hodnoty, nebude dostupná, dokud nebude **DataReader –** je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="646ab-116">If your **Command** contains output parameters or return values, they will not be available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="646ab-117">Všimněte si, že chvíli **DataReader –** je otevřený **připojení** se používá výhradně v tomto **DataReader –**.</span><span class="sxs-lookup"><span data-stu-id="646ab-117">Note that while a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="646ab-118">Nelze provést žádné příkazy pro **připojení**, včetně vytváření jiného **DataReader –**, dokud nebude původní **DataReader –** je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="646ab-118">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="646ab-119">Nevolejte **Zavřít** nebo **Dispose** na **připojení**, **DataReader –**, nebo jiné spravovaného objektu v **dokončení**  metoda vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="646ab-119">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="646ab-120">V finalizační metodu vydání pouze nespravovaných prostředků, které vlastní třídu přímo.</span><span class="sxs-lookup"><span data-stu-id="646ab-120">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="646ab-121">Pokud vaše třída nevlastní žádné nespravovaných prostředků, nezahrnujte **Finalize** metoda v definici vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="646ab-121">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="646ab-122">Další informace najdete v tématu [uvolňování paměti](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="646ab-122">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="646ab-123">Načítání více sad výsledků dotazu pomocí NextResult</span><span class="sxs-lookup"><span data-stu-id="646ab-123">Retrieving Multiple Result Sets using NextResult</span></span>  
 <span data-ttu-id="646ab-124">Pokud jsou vráceny více sad výsledků dotazu, **DataReader –** poskytuje **NextResult** metoda k iteraci v rámci výsledek nastaví v pořadí.</span><span class="sxs-lookup"><span data-stu-id="646ab-124">If multiple result sets are returned, the **DataReader** provides the **NextResult** method to iterate through the result sets in order.</span></span> <span data-ttu-id="646ab-125">Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků pomocí dvou příkazů SELECT <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="646ab-125">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="646ab-126">Získávání informací o schématu z objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="646ab-126">Getting Schema Information from the DataReader</span></span>  
 <span data-ttu-id="646ab-127">Při **DataReader –** je otevřená, můžete načíst informace o schématu o aktuální výsledek nastavit pomocí **GetSchemaTable** metoda.</span><span class="sxs-lookup"><span data-stu-id="646ab-127">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="646ab-128">**GetSchemaTable** vrátí <xref:System.Data.DataTable> objekt naplněný řádků a sloupců, které obsahují informace o schématu pro aktuální sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="646ab-128">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="646ab-129">**DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="646ab-129">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="646ab-130">Každý sloupec řádku tabulky schématu je namapován na vlastnost sloupec, vrátí se v nastavit výsledek, kde **ColumnName** je název vlastnosti a hodnota sloupce je hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="646ab-130">Each column of the schema table row maps to a property of the column returned in the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="646ab-131">Následující příklad kódu zapíše informace o schématu **DataReader –**.</span><span class="sxs-lookup"><span data-stu-id="646ab-131">The following code example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="646ab-132">Práce s kapitolám OLE DB</span><span class="sxs-lookup"><span data-stu-id="646ab-132">Working with OLE DB Chapters</span></span>  
 <span data-ttu-id="646ab-133">Hierarchická sady řádků či kapitolám (typ OLE DB **DBTYPE_HCHAPTER**, ADO typ **adChapter**) se dá načíst pomocí <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="646ab-133">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**) can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="646ab-134">Pokud se dotaz, který zahrnuje kapitola vrátí jako **DataReader –**, kapitoly je vrácen jako sloupec v tom, že **DataReader –** a je k dispozici jako **DataReader** objektu.</span><span class="sxs-lookup"><span data-stu-id="646ab-134">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="646ab-135">Technologie ADO.NET **datovou sadu** lze také použít k reprezentaci hierarchické sady řádků pomocí vztahů nadřazenosti a podřízenosti mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="646ab-135">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets using parent-child relationships between tables.</span></span> <span data-ttu-id="646ab-136">Další informace najdete v tématu [datové sady, DataTables a DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="646ab-136">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="646ab-137">Následující příklad kódu používá zprostředkovatele MSDataShape ke generování objednávek každému zákazníkovi neočekávaný sloupec kapitoly v seznamu zákazníků.</span><span class="sxs-lookup"><span data-stu-id="646ab-137">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="646ab-138">Vrátí výsledky s kurzory REF Oracle</span><span class="sxs-lookup"><span data-stu-id="646ab-138">Returning Results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="646ab-139">Zprostředkovatel dat .NET Framework pro Oracle podporuje použití Oracle REF kurzory vrácení výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="646ab-139">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="646ab-140">V Oracle REF kurzor se vrátí jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="646ab-140">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="646ab-141">Můžete načíst **připojení OracleDataReader** objekt, který představuje k KURZORU REF Oracle pomocí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metodu a můžete také zadat <xref:System.Data.OracleClient.OracleCommand> , který vrací jeden nebo více kurzory REF Oracle jako  **SelectCommand** pro <xref:System.Data.OracleClient.OracleDataAdapter> použitou k vyplnění <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="646ab-141">You can retrieve an **OracleDataReader** object, that represents an Oracle REF CURSOR using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method, and you can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="646ab-142">Pro přístup k KURZORU REF vrátí ze zdroje dat Oracle, vytvořit **OracleCommand** pro svůj dotaz a přidejte výstupní parametr, který odkazuje na REF ukazatele **parametry** kolekce vaší  **OracleCommand**.</span><span class="sxs-lookup"><span data-stu-id="646ab-142">To access a REF CURSOR returned from an Oracle data source, create an **OracleCommand** for your query and add an output parameter that references the REF CURSOR to the **Parameters** collection of your **OracleCommand**.</span></span> <span data-ttu-id="646ab-143">Název parametru musí odpovídat názvu parametru REF KURZORU v dotazu.</span><span class="sxs-lookup"><span data-stu-id="646ab-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="646ab-144">Nastavte typ parametru **OracleType.Cursor**.</span><span class="sxs-lookup"><span data-stu-id="646ab-144">Set the type of the parameter to **OracleType.Cursor**.</span></span> <span data-ttu-id="646ab-145">**ExecuteReader** metodu vaše **OracleCommand** vrátí **připojení OracleDataReader** pro kurzor REF.</span><span class="sxs-lookup"><span data-stu-id="646ab-145">The **ExecuteReader** method of your **OracleCommand** will return an **OracleDataReader** for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="646ab-146">Pokud vaše **OracleCommand** vrátí více REF kurzory, přidat více výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="646ab-146">If your **OracleCommand** returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="646ab-147">Různé kurzory REF můžete přejít pomocí volání **OracleCommand.ExecuteReader** metoda.</span><span class="sxs-lookup"><span data-stu-id="646ab-147">You can access the different REF CURSORs by calling the **OracleCommand.ExecuteReader** method.</span></span> <span data-ttu-id="646ab-148">Volání **ExecuteReader** vrátí **připojení OracleDataReader** odkazující na první REF kurzor.</span><span class="sxs-lookup"><span data-stu-id="646ab-148">The call to **ExecuteReader** returns an **OracleDataReader** referencing the first REF CURSOR.</span></span> <span data-ttu-id="646ab-149">Potom můžete zavolat **OracleDataReader.NextResult** metody přístup následné REF kurzory.</span><span class="sxs-lookup"><span data-stu-id="646ab-149">You can then call the **OracleDataReader.NextResult** method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="646ab-150">I když parametry ve vaší **OracleCommand.Parameters** kolekce shodu kurzor REF výstupní parametry podle názvu, **připojení OracleDataReader** k nim přistupuje v pořadí, aby byly přidány do  **Parametry** kolekce.</span><span class="sxs-lookup"><span data-stu-id="646ab-150">Although the parameters in your **OracleCommand.Parameters** collection match the REF CURSOR output parameters by name, the **OracleDataReader** accesses them in the order that they were added to the **Parameters** collection.</span></span>  
  
 <span data-ttu-id="646ab-151">Zvažte například následující balíček Oracle a tělo balíčku.</span><span class="sxs-lookup"><span data-stu-id="646ab-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="646ab-152">Následující kód vytvoří **OracleCommand** , vrátí kurzory REF z předchozí balíčku Oracle přidáním dva parametry typu **OracleType.Cursor** k **parametry** kolekce.</span><span class="sxs-lookup"><span data-stu-id="646ab-152">The following code creates an **OracleCommand** that returns the REF CURSORs from the previous Oracle package by adding two parameters of type **OracleType.Cursor** to the **Parameters** collection.</span></span>  
  
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
  
 <span data-ttu-id="646ab-153">Následující kód vrátí výsledky předchozí příkaz pomocí **čtení** a **NextResult** metody **připojení OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="646ab-153">The following code returns the results of the previous command using the **Read** and **NextResult** methods of the **OracleDataReader**.</span></span> <span data-ttu-id="646ab-154">Parametry KURZORU REF jsou vráceny v pořadí.</span><span class="sxs-lookup"><span data-stu-id="646ab-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="646ab-155">Následující příklad používá předchozí příkaz k naplnění **datovou sadu** s výsledky balíčku Oracle.</span><span class="sxs-lookup"><span data-stu-id="646ab-155">The following example uses the previous command to populate a **DataSet** with the results of the Oracle package.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="646ab-156">Aby nedošlo **OverflowException**, doporučujeme také zpracovat žádné převod z typu Oracle číslo na platný typ rozhraní .NET Framework před uložením hodnoty v **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="646ab-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a **DataRow**.</span></span> <span data-ttu-id="646ab-157">Můžete použít **FillError** událostí k určení, zda **OverflowException** došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="646ab-157">You can use the **FillError** event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="646ab-158">Další informace o **FillError** událostí, najdete v části [zpracování události DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="646ab-158">For more information on the **FillError** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="646ab-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="646ab-159">See Also</span></span>  
 [<span data-ttu-id="646ab-160">Práce s DataReaders</span><span class="sxs-lookup"><span data-stu-id="646ab-160">Working with DataReaders</span></span>](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="646ab-161">DataAdapters a DataReaders</span><span class="sxs-lookup"><span data-stu-id="646ab-161">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="646ab-162">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="646ab-162">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="646ab-163">Načítání informací o schématu databáze</span><span class="sxs-lookup"><span data-stu-id="646ab-163">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="646ab-164">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="646ab-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
