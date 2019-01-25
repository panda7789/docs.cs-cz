---
title: Načítání dat pomocí čtečky dat
ms.date: 10/259/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 134bb68b9cf60cc5082afefdd9eb87d991b6e0ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692753"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="8b0a9-102">Načtení dat pomocí čtečky dat</span><span class="sxs-lookup"><span data-stu-id="8b0a9-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="8b0a9-103">K načtení dat pomocí **DataReader**, vytvoření instance **příkaz** objektu a pak vytvořte **DataReader** voláním **Command.ExecuteReader**  načíst ze zdroje dat řádků.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="8b0a9-104">**DataReader** poskytuje bez vyrovnávací paměti datového proudu dat, která umožňuje procedurální logiku pro efektivní zpracování výsledků ze zdroje dat postupně.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="8b0a9-105">**DataReader** je dobrou volbou, pokud načítáte velkých objemů dat, protože data neukládají do mezipaměti v paměti.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="8b0a9-106">Následující příklad ukazuje použití **DataReader**, kde `reader` představuje platné čtečky dat a `command` představuje objekt platný příkaz.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="8b0a9-107">Použití **DataReader.Read** metoda získat řádek z výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="8b0a9-108">Každý sloupec vrácený řádek se zpřístupní po předání názvu nebo ordinální číslo sloupce, který se **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="8b0a9-109">Ale pro zajištění nejlepšího výkonu **DataReader** poskytuje řadu metod, které umožňují přístup k hodnot sloupce v jejich nativním datové typy (**GetDateTime**, **GetDouble**, **Getguid –**, **GetInt32**, a tak dále).</span><span class="sxs-lookup"><span data-stu-id="8b0a9-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="8b0a9-110">Seznam typu přístupové metody pro data specifickým pro zprostředkovatele **čtečky dat**, naleznete v tématu <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="8b0a9-111">Pomocí metod typu přístupového objektu, když víte, podkladová data typu snižuje počet při načítání hodnoty sloupce vyžaduje převod typů.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="8b0a9-112">Následující příklad provede iteraci **DataReader** a vrátí dva sloupce z každého řádku.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="8b0a9-113">Zavření objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="8b0a9-113">Closing the DataReader</span></span>  
 <span data-ttu-id="8b0a9-114">Vždy volat **Zavřít** metoda po dokončení používání **DataReader** objektu.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="8b0a9-115">Pokud vaše **příkaz** obsahuje výstupní parametry nebo návratové hodnoty, tyto hodnoty nejsou k dispozici, dokud **DataReader** je zavřený.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="8b0a9-116">Při **DataReader** je otevřený, **připojení** používá výhradně, který **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="8b0a9-117">Nelze provést žádné příkazy pro **připojení**, včetně vytvoříte další **DataReader**, dokud původní **DataReader** je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b0a9-118">Nevolejte **Zavřít** nebo **Dispose** na **připojení**, **DataReader**, nebo jakýkoli jiný spravovaný objekt v **Finalize**  metoda vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="8b0a9-119">V finalizační metodu jenom uvolnění nespravovaných prostředků, které vaše třída vlastní přímo.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="8b0a9-120">Pokud vaše třída není vlastníkem jakýchkoliv nespravovaných prostředků, nezahrnujte **Finalize** metoda v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="8b0a9-121">Další informace najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="8b0a9-121">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="8b0a9-122">Načítání více výsledků nastaví pomocí NextResult</span><span class="sxs-lookup"><span data-stu-id="8b0a9-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="8b0a9-123">Pokud **DataReader** vrátí více sad výsledků dotazu, volání **NextResult** metoda procházením skrze výsledek nastaví postupně.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="8b0a9-124">Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků pomocí dvou příkazů SELECT <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="8b0a9-125">Získávání informací o schématu z objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="8b0a9-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="8b0a9-126">Při **DataReader** je otevřít, můžete načíst informace o schématu o aktuální výsledek sada s použitím **GetSchemaTable** metoda.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="8b0a9-127">**GetSchemaTable** vrátí <xref:System.Data.DataTable> objekt naplní řádky a sloupce, které obsahují informace o schématu pro aktuální sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="8b0a9-128">**DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="8b0a9-129">Každý sloupec v tabulce schématu se mapuje na vlastnost sloupců vrácených v řádky výsledek nastavit, kam **Názevsloupce** je název vlastnosti a hodnota sloupce je hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="8b0a9-130">Následující příklad zapíše informace o schématu pro **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="8b0a9-131">Práce s kapitol OLE DB</span><span class="sxs-lookup"><span data-stu-id="8b0a9-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="8b0a9-132">Hierarchické sady řádků nebo kapitol (typ OLE DB **DBTYPE_HCHAPTER**, typ ADO **adChapter**), můžete získat pomocí <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="8b0a9-133">Při dotazu, který zahrnuje kapitola se vrátí jako **DataReader**, kapitoly je vrácen jako sloupec, který **DataReader** a je přístupný jako **DataReader** objektu.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="8b0a9-134">ADO.NET **datovou sadu** lze také použít k reprezentaci hierarchické sady řádků pomocí vztahů nadřazenosti a podřízenosti mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="8b0a9-135">Další informace najdete v tématu [datové sady, datové tabulky a zobrazení dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="8b0a9-135">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="8b0a9-136">Následující příklad kódu používá zprostředkovatele MSDataShape ke generování objednávek pro každého zákazníka neočekávaný sloupec kapitoly v seznam zákazníků.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="8b0a9-137">Vrací výsledky s soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="8b0a9-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="8b0a9-138">Zprostředkovatel dat .NET Framework pro Oracle podporuje použití soubory Oracle REF CURSOR vrácení výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="8b0a9-139">Vrátí se Oracle REF CURSOR jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="8b0a9-140">Můžete načíst <xref:System.Data.OracleClient.OracleDataReader> objekt, který představuje Oracle REF CURSOR pomocí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="8b0a9-141">Můžete také určit, <xref:System.Data.OracleClient.OracleCommand> , který vrací jeden nebo více soubory Oracle REF CURSOR jako **SelectCommand** pro <xref:System.Data.OracleClient.OracleDataAdapter> použitou k vyplnění <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="8b0a9-142">Pro přístup k REF CURSOR vrácená ze zdroje dat Oracle, vytvořte <xref:System.Data.OracleClient.OracleCommand> pro váš dotaz a přidejte výstupní parametr, který odkazuje kurzor REF <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekce vaše <xref:System.Data.OracleClient.OracleCommand>.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="8b0a9-143">Název parametru musí odpovídat názvu parametru REF CURSOR v dotazu.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="8b0a9-144">Nastavit typ parametru <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8b0a9-145"><xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> Metodu vaše <xref:System.Data.OracleClient.OracleCommand> vrátí <xref:System.Data.OracleClient.OracleDataReader> pro REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="8b0a9-146">Pokud vaše <xref:System.Data.OracleClient.OracleCommand> vrací více typů REF CURSOR, přidat více výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="8b0a9-147">Dostanete různých typů REF CURSOR pomocí volání <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8b0a9-148">Volání <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> vrátí <xref:System.Data.OracleClient.OracleDataReader> odkazující na první REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="8b0a9-149">Potom můžete zavolat <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> metody pro přístup k dalších typů REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="8b0a9-150">I když parametry v vaše <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekce shoda REF CURSOR output parametry podle názvu, <xref:System.Data.OracleClient.OracleDataReader> k nim přistupuje, v pořadí, ve kterém byly přidány do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekce.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="8b0a9-151">Představte si třeba následující balíček Oracle a tělo balíčku.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="8b0a9-152">Následující kód vytvoří <xref:System.Data.OracleClient.OracleCommand> typů REF CURSOR z předchozí balíčku Oracle, který vrací tak, že přidáte dva parametry typu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> k <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="8b0a9-153">Následující kód vrátí výsledky z předchozího příkazu s <xref:System.Data.OracleClient.OracleDataReader.Read> a <xref:System.Data.OracleClient.OracleDataReader.NextResult> metody <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="8b0a9-154">Parametry REF CURSOR jsou vráceny v pořadí.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="8b0a9-155">Následující příklad používá k naplnění předchozí příkaz <xref:System.Data.DataSet> s výsledky balíčku Oracle.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
>  <span data-ttu-id="8b0a9-156">Aby se zabránilo **OverFlowException –**, doporučujeme také zpracovat jakýkoli převod z typu Oracle číslo na platný typ rozhraní .NET Framework před uložením hodnoty v <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="8b0a9-157">Můžete použít <xref:System.Data.Common.DataAdapter.FillError> událostí k určení, zda **OverFlowException –** došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="8b0a9-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="8b0a9-158">Další informace o <xref:System.Data.Common.DataAdapter.FillError> událostí, naleznete v tématu [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="8b0a9-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b0a9-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b0a9-159">See also</span></span>
- [<span data-ttu-id="8b0a9-160">Práce s čtečky dat</span><span class="sxs-lookup"><span data-stu-id="8b0a9-160">Working with DataReaders</span></span>](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)
- [<span data-ttu-id="8b0a9-161">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="8b0a9-161">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="8b0a9-162">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="8b0a9-162">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="8b0a9-163">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="8b0a9-163">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="8b0a9-164">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8b0a9-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
