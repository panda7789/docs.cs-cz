---
title: Načítání dat pomocí čtečky dat
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 561ebd7ac6948fa42f73ebb4f1eb97c574e6d7e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963165"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="81be3-102">Načtení dat pomocí datového objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="81be3-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="81be3-103">Chcete-li načíst datapomocí objektu DataReader, vytvořte instanci **objektu Command** a pak vytvořte objekt DataReader voláním **příkazu Command. ExecuteReader** pro načtení řádků ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="81be3-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="81be3-104">Objekt **DataReader** poskytuje datový proud bez vyrovnávací paměti, který umožňuje procedurální logice efektivně zpracovávat výsledky ze zdroje dat postupně.</span><span class="sxs-lookup"><span data-stu-id="81be3-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="81be3-105">Objekt **DataReader** je dobrou volbou při načítání velkých objemů dat, protože data nejsou ukládána v paměti.</span><span class="sxs-lookup"><span data-stu-id="81be3-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="81be3-106">Následující příklad znázorňuje použití objektu DataReader, který `reader` představuje platný objekt DataReader `command` a představuje platný objekt příkazu.</span><span class="sxs-lookup"><span data-stu-id="81be3-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="81be3-107">K získání řádku z výsledků dotazu použijte metodu **DataReader. Read** .</span><span class="sxs-lookup"><span data-stu-id="81be3-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="81be3-108">Do každého sloupce vráceného řádku můžete přistupovat předáním názvu nebo pořadového čísla sloupce do objektu DataReader.</span><span class="sxs-lookup"><span data-stu-id="81be3-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="81be3-109">Pro nejlepší výkon ale DataReader poskytuje řadu metod, které umožňují přístup k hodnotám sloupců v jejich nativních datových typech (GetDateTime, GetDouble, GetGUID, GetInt32a tak dále).</span><span class="sxs-lookup"><span data-stu-id="81be3-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="81be3-110">Seznam typových přístupových metod pro datačtecí metody specifických proposkytovatele dat naleznete v tématech <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="81be3-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="81be3-111">Použití typových přístupových metod, pokud víte, že podkladový datový typ snižuje množství konverze typu požadované při načítání hodnoty sloupce.</span><span class="sxs-lookup"><span data-stu-id="81be3-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="81be3-112">Následující příklad provede iteraci objektu **DataReader** a vrátí dva sloupce z každého řádku.</span><span class="sxs-lookup"><span data-stu-id="81be3-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="81be3-113">Zavření objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="81be3-113">Closing the DataReader</span></span>  
 <span data-ttu-id="81be3-114">Po dokončení používání objektu DataReader vždy zavolejte metodu **Close** .</span><span class="sxs-lookup"><span data-stu-id="81be3-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="81be3-115">Pokud váš **příkaz** obsahuje výstupní parametry nebo návratové hodnoty, tyto hodnoty nejsou k dispozici , dokud není DataReader uzavřen.</span><span class="sxs-lookup"><span data-stu-id="81be3-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="81be3-116">Když je objekt DataReader otevřený, **připojení** je používáno výhradně tímto objektem DataReader.</span><span class="sxs-lookup"><span data-stu-id="81be3-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="81be3-117">Pro **připojení**nemůžete spustit žádné příkazy, včetně vytvoření jinéhoobjektu DataReader, dokud nebude původní DataReader uzavřený.</span><span class="sxs-lookup"><span data-stu-id="81be3-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81be3-118">Nevolejte funkci **Close** nebo **Dispose** pro **připojení**, objekt **DataReader**nebo jakýkoli jiný spravovaný objekt v metodě **Finalize** třídy.</span><span class="sxs-lookup"><span data-stu-id="81be3-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="81be3-119">V finalizační metodě pouze uvolní nespravované prostředky, které vaše třída vlastní.</span><span class="sxs-lookup"><span data-stu-id="81be3-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="81be3-120">Pokud vaše třída nevlastní žádné nespravované prostředky, nezahrnujte do definice třídy metodu **Finalize** .</span><span class="sxs-lookup"><span data-stu-id="81be3-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="81be3-121">Další informace najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="81be3-121">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="81be3-122">Načítání více sad výsledků pomocí NextResult</span><span class="sxs-lookup"><span data-stu-id="81be3-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="81be3-123">Pokud **DataReader** vrátí více sad výsledků, zavolejte metodu **NextResult** pro iteraci skrze sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="81be3-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="81be3-124">Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků dvou příkazů Select <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="81be3-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="81be3-125">Získávání informací o schématu z objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="81be3-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="81be3-126">Když je objekt DataReader otevřený, můžete načíst informace o schématu aktuální sady výsledků pomocí metody GetSchema.</span><span class="sxs-lookup"><span data-stu-id="81be3-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="81be3-127">GetSchemas vrátí <xref:System.Data.DataTable> objekt naplněný řádky a sloupci, které obsahují informace o schématu pro aktuální sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="81be3-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="81be3-128">**Objekt DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="81be3-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="81be3-129">Každý sloupec tabulky schématu se mapuje na vlastnost sloupců vrácených v řádcích sady výsledků, kde **ColumnName** je název vlastnosti a hodnota sloupce je hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81be3-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="81be3-130">Následující příklad vypíše informace o schématu pro **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="81be3-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="81be3-131">Práce s OLE DB kapitolami</span><span class="sxs-lookup"><span data-stu-id="81be3-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="81be3-132">Hierarchické sady řádků nebo kapitoly (OLE DB typu **DBTYPE_HCHAPTER**, ADO Type **adChapter**), lze <xref:System.Data.OleDb.OleDbDataReader>načíst pomocí.</span><span class="sxs-lookup"><span data-stu-id="81be3-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="81be3-133">Pokud je jako objekt DataReader vrácen dotaz, který obsahujekapitolu, je tato kapitola vrácena jako sloupec v objektu **DataReader** a je vystavena jako objekt DataReader.</span><span class="sxs-lookup"><span data-stu-id="81be3-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="81be3-134">Datovou **sadu** ADO.NET lze také použít k reprezentaci hierarchických sad řádků pomocí vztahů nadřazenosti a podřízenosti mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="81be3-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="81be3-135">Další informace najdete v tématu [datové sady, datové tabulky a datazobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="81be3-135">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="81be3-136">Následující příklad kódu používá poskytovatele MSDataShape k vygenerování sloupce kapitoly objednávek pro každého zákazníka v seznamu zákazníků.</span><span class="sxs-lookup"><span data-stu-id="81be3-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="81be3-137">Vracení výsledků pomocí REFERENČNÍch KURZORů Oracle</span><span class="sxs-lookup"><span data-stu-id="81be3-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="81be3-138">Zprostředkovatel dat .NET Framework pro Oracle podporuje použití odkazů Oracle REF CURSOR k vrácení výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="81be3-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="81be3-139">Referenční kurzor Oracle se vrátí jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="81be3-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="81be3-140"><xref:System.Data.OracleClient.OracleDataReader> Objekt, který představuje referenční kurzor Oracle, můžete načíst <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="81be3-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="81be3-141">Můžete také zadat <xref:System.Data.OracleClient.OracleCommand> , který vrátí jeden nebo více referenčních kurzorů Oracle <xref:System.Data.OracleClient.OracleDataAdapter> jako **vlastnost SelectCommand** , která se používá k naplnění <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="81be3-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="81be3-142">Chcete-li získat přístup k referenčnímu ukazateli vrácenému ze zdroje <xref:System.Data.OracleClient.OracleCommand> dat Oracle, vytvořte pro dotaz dotaz a přidejte výstupní parametr, který odkazuje na <xref:System.Data.OracleClient.OracleCommand.Parameters> ukazatel ref na <xref:System.Data.OracleClient.OracleCommand>kolekci vaší.</span><span class="sxs-lookup"><span data-stu-id="81be3-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="81be3-143">Název parametru se musí shodovat s názvem parametru REF CURSOR v dotazu.</span><span class="sxs-lookup"><span data-stu-id="81be3-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="81be3-144">Nastavte typ parametru na <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81be3-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="81be3-145">Metoda vašeho <xref:System.Data.OracleClient.OracleCommand> vrátí<xref:System.Data.OracleClient.OracleDataReader> pro kurzor ref. <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="81be3-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="81be3-146"><xref:System.Data.OracleClient.OracleCommand> Pokud vrátí více ukazatelů ref, přidejte více výstupních parametrů.</span><span class="sxs-lookup"><span data-stu-id="81be3-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="81be3-147">Můžete získat přístup k různým odkazovým Kurzorům voláním <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="81be3-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="81be3-148"><xref:System.Data.OracleClient.OracleCommand.ExecuteReader> Volání<xref:System.Data.OracleClient.OracleDataReader> funkce vrátí odkaz na první odkazový kurzor.</span><span class="sxs-lookup"><span data-stu-id="81be3-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="81be3-149">Pak můžete zavolat <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> metodu pro přístup k dalším odkazovým Kurzorům.</span><span class="sxs-lookup"><span data-stu-id="81be3-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="81be3-150">I když parametry ve vaší <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekci odpovídají výstupním parametrům REF CURSOR podle názvu <xref:System.Data.OracleClient.OracleDataReader> , přistupuje je v pořadí, ve kterém byly přidány do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekce.</span><span class="sxs-lookup"><span data-stu-id="81be3-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="81be3-151">Zvažte například následující balíček Oracle a tělo balíčku.</span><span class="sxs-lookup"><span data-stu-id="81be3-151">For example, consider the following Oracle package and package body.</span></span>  
  
```sql
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
  
 <span data-ttu-id="81be3-152">Následující kód vytvoří objekt <xref:System.Data.OracleClient.OracleCommand> , který vrátí referenční kurzory z předchozího balíčku Oracle přidáním dvou parametrů typu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> do <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="81be3-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="81be3-153">Následující kód vrátí výsledky předchozího příkazu pomocí <xref:System.Data.OracleClient.OracleDataReader.Read> metody <xref:System.Data.OracleClient.OracleDataReader>a <xref:System.Data.OracleClient.OracleDataReader.NextResult> .</span><span class="sxs-lookup"><span data-stu-id="81be3-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="81be3-154">Parametry REF CURSOR jsou vráceny v pořadí.</span><span class="sxs-lookup"><span data-stu-id="81be3-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="81be3-155">Následující příklad používá předchozí příkaz k naplnění <xref:System.Data.DataSet> výsledků balíčku Oracle.</span><span class="sxs-lookup"><span data-stu-id="81be3-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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

> [!NOTE]
> <span data-ttu-id="81be3-156">Abyste se vyhnuli **OverflowException**, doporučujeme, abyste před uložením hodnoty v <xref:System.Data.DataRow>. také pokaždé konverze z typu čísla Oracle na platný typ .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81be3-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="81be3-157"><xref:System.Data.Common.DataAdapter.FillError> Událost můžete použít k určení, zda došlo k **OverflowException** .</span><span class="sxs-lookup"><span data-stu-id="81be3-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="81be3-158">Další informace o <xref:System.Data.Common.DataAdapter.FillError> události naleznete v tématu [zpracování událostí DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="81be3-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81be3-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81be3-159">See also</span></span>

- [<span data-ttu-id="81be3-160">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="81be3-160">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="81be3-161">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="81be3-161">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="81be3-162">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="81be3-162">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="81be3-163">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="81be3-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
