---
title: Načítání dat pomocí čtečky dat
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 88cd85ce343aaab08b944f81c9659918014da0a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149021"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="defa0-102">Načtení dat pomocí datareaderu</span><span class="sxs-lookup"><span data-stu-id="defa0-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="defa0-103">Chcete-li načíst data pomocí **datareaderu**, vytvořte instanci objektu **Příkaz** a pak **vytvořte datareader** voláním **Příkaz.ExecuteReader** pro načtení řádků ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="defa0-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="defa0-104">**DataReader** poskytuje bez vyrovnávací proud dat, který umožňuje procedurální logiku efektivně zpracovávat výsledky ze zdroje dat postupně.</span><span class="sxs-lookup"><span data-stu-id="defa0-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="defa0-105">**DataReader** je dobrou volbou při načítání velkého množství dat, protože data nejsou uložena v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="defa0-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="defa0-106">Následující příklad ilustruje použití **DataReader** `reader` , kde představuje `command` platný DataReader a představuje platný objekt Příkaz.</span><span class="sxs-lookup"><span data-stu-id="defa0-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="defa0-107">Pomocí metody **DataReader.Read** získáte řádek z výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="defa0-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="defa0-108">Ke každému sloupci vráceného řádku můžete přistupovat předáním názvu nebo číslo čísla sloupce **aplikaci DataReader**.</span><span class="sxs-lookup"><span data-stu-id="defa0-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="defa0-109">Pro nejlepší výkon však **DataReader** poskytuje řadu metod, které umožňují přístup k hodnotám sloupců v jejich nativní datové typy **(GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**a tak dále).</span><span class="sxs-lookup"><span data-stu-id="defa0-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="defa0-110">Seznam metod přístupového operátoru typu pro datové čtečky <xref:System.Data.OleDb.OleDbDataReader> <xref:System.Data.SqlClient.SqlDataReader>specifické pro zprostředkovatele dat naleznete v **tématu**a .</span><span class="sxs-lookup"><span data-stu-id="defa0-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="defa0-111">Použití zadávaných přistupovacích metod, pokud znáte základní datový typ, snižuje množství převodu typu, který je nutný při načítání hodnoty sloupce.</span><span class="sxs-lookup"><span data-stu-id="defa0-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="defa0-112">Následující příklad itetuje prostřednictvím objektu **DataReader** a vrátí dva sloupce z každého řádku.</span><span class="sxs-lookup"><span data-stu-id="defa0-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="defa0-113">Zavření čtečky dat</span><span class="sxs-lookup"><span data-stu-id="defa0-113">Closing the DataReader</span></span>  
 <span data-ttu-id="defa0-114">Po dokončení použití objektu **DataReader** vždy zavolejte metodu **Close.**</span><span class="sxs-lookup"><span data-stu-id="defa0-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="defa0-115">Pokud **příkaz** obsahuje výstupní parametry nebo vrácené hodnoty, tyto hodnoty nejsou k dispozici, dokud **datareader** je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="defa0-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="defa0-116">Při **datareader** je **otevřena, připojení** je používán výhradně, že **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="defa0-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="defa0-117">Nelze spustit žádné příkazy pro **připojení**, včetně vytvoření jiné **datareader**, dokud původní **DataReader** je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="defa0-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="defa0-118">Nevolat **Close** nebo **Dispose** na **připojení**, **DataReader**nebo jakýkoli jiný spravovaný objekt v **Finalize** metoda vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="defa0-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="defa0-119">Ve finalizační metodě uvolněte pouze nespravované prostředky, které přímo vlastní vaše třída.</span><span class="sxs-lookup"><span data-stu-id="defa0-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="defa0-120">Pokud vaše třída nevlastní žádné nespravované prostředky, nezahrnujte metodu **Finalize** do definice třídy.</span><span class="sxs-lookup"><span data-stu-id="defa0-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="defa0-121">Další informace naleznete v [tématu Garbage Collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="defa0-121">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="defa0-122">Načítání více sad výsledků pomocí funkce NextResult</span><span class="sxs-lookup"><span data-stu-id="defa0-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="defa0-123">Pokud **DataReader** vrátí více sad výsledků, volejte **NextResult** metoda iterát prostřednictvím sady výsledků postupně.</span><span class="sxs-lookup"><span data-stu-id="defa0-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="defa0-124">Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků dvou příkazů <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> SELECT pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="defa0-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="defa0-125">Získání informací o schématu z datareaderu</span><span class="sxs-lookup"><span data-stu-id="defa0-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="defa0-126">Když je otevřena **datareader,** můžete načíst informace o schématu o aktuální sadě výsledků pomocí **metody GetSchemaTable.**</span><span class="sxs-lookup"><span data-stu-id="defa0-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="defa0-127">**GetSchemaTable** vrátí <xref:System.Data.DataTable> objekt naplněný řádky a sloupci, které obsahují informace o schématu pro aktuální sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="defa0-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="defa0-128">**DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="defa0-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="defa0-129">Každý sloupec tabulky schématu mapuje na vlastnost sloupců vrácených v řádcích sady výsledků, kde **ColumnName** je název vlastnosti a hodnota sloupce je hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="defa0-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="defa0-130">Následující příklad zapíše informace o schématu pro **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="defa0-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="defa0-131">Práce s kapitolami TECHNOLOGIE OLE DB</span><span class="sxs-lookup"><span data-stu-id="defa0-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="defa0-132">Hierarchické sady řádků nebo kapitoly (typ OLE DB **DBTYPE_HCHAPTER**, **adChapter**typu <xref:System.Data.OleDb.OleDbDataReader>ADO ) lze načíst pomocí .</span><span class="sxs-lookup"><span data-stu-id="defa0-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="defa0-133">Pokud je dotaz, který obsahuje kapitolu, vrácen jako **DataReader**, je tato kapitola vrácena jako sloupec v této **aplikaci DataReader** a je vystavena jako objekt **DataReader.**</span><span class="sxs-lookup"><span data-stu-id="defa0-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="defa0-134">ADO.NET **DataSet** lze také použít k reprezentaci hierarchické sady řádků pomocí relace nadřazený podřízený mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="defa0-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="defa0-135">Další informace naleznete v [tématu DataSets, DataTables a DataViews](./dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="defa0-135">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="defa0-136">Následující příklad kódu používá zprostředkovatele MSDataShape ke generování sloupce kapitol objednávek pro každého zákazníka v seznamu zákazníků.</span><span class="sxs-lookup"><span data-stu-id="defa0-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="defa0-137">Vrácení výsledků pomocí řešení Oracle REF CURSORs</span><span class="sxs-lookup"><span data-stu-id="defa0-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="defa0-138">Zprostředkovatel dat rozhraní .NET Framework pro oracle podporuje použití řešení Oracle REF CURSORs k vrácení výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="defa0-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="defa0-139">Oracle REF CURSOR je <xref:System.Data.OracleClient.OracleDataReader>vrácena jako .</span><span class="sxs-lookup"><span data-stu-id="defa0-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="defa0-140">Pomocí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody <xref:System.Data.OracleClient.OracleDataReader> můžete načíst objekt, který představuje Oracle REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="defa0-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="defa0-141"><xref:System.Data.OracleClient.OracleCommand> Můžete také určit, který vrátí jeden nebo více Řešení REF CURSORs jako **SelectCommand** pro <xref:System.Data.OracleClient.OracleDataAdapter> slouží k vyplnění . <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="defa0-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="defa0-142">Chcete-li získat přístup k ref cursor <xref:System.Data.OracleClient.OracleCommand> vrácené ze zdroje dat Oracle, vytvořte pro <xref:System.Data.OracleClient.OracleCommand.Parameters> dotaz <xref:System.Data.OracleClient.OracleCommand>a přidejte výstupní parametr, který odkazuje na KURZOR REF na kolekci vašeho .</span><span class="sxs-lookup"><span data-stu-id="defa0-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="defa0-143">Název parametru se musí shodovat s názvem parametru REF CURSOR v dotazu.</span><span class="sxs-lookup"><span data-stu-id="defa0-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="defa0-144">Nastavte typ parametru <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>na .</span><span class="sxs-lookup"><span data-stu-id="defa0-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="defa0-145">Metoda <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> vrátí <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader> pro REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="defa0-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="defa0-146">Pokud <xref:System.Data.OracleClient.OracleCommand> vrátí více REF CURSORS, přidejte více výstupních parametrů.</span><span class="sxs-lookup"><span data-stu-id="defa0-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="defa0-147">Můžete přistupovat k různým REF CURSORs voláním <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="defa0-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="defa0-148">Volání vrátí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> <xref:System.Data.OracleClient.OracleDataReader> odkazující na první KURZOR REF.</span><span class="sxs-lookup"><span data-stu-id="defa0-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="defa0-149">Potom můžete volat <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> metodu pro přístup k následné REF CURSORs.</span><span class="sxs-lookup"><span data-stu-id="defa0-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="defa0-150">Přestože parametry <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> v kolekci odpovídají výstupní parametry <xref:System.Data.OracleClient.OracleDataReader> REF CURSOR podle názvu, přistupuje k nim v pořadí, ve kterém byly přidány do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekce.</span><span class="sxs-lookup"><span data-stu-id="defa0-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="defa0-151">Zvažte například následující oracle balíček a balíček tělo.</span><span class="sxs-lookup"><span data-stu-id="defa0-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="defa0-152">Následující kód vytvoří, <xref:System.Data.OracleClient.OracleCommand> který vrátí REF CURSORs z předchozího balíčku <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> Oracle <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> přidáním dvou parametrů typu do kolekce.</span><span class="sxs-lookup"><span data-stu-id="defa0-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="defa0-153">Následující kód vrátí výsledky předchozího <xref:System.Data.OracleClient.OracleDataReader.Read> příkazu <xref:System.Data.OracleClient.OracleDataReader.NextResult> pomocí <xref:System.Data.OracleClient.OracleDataReader>metody a .</span><span class="sxs-lookup"><span data-stu-id="defa0-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="defa0-154">Parametry REF CURSOR jsou vráceny v pořadí.</span><span class="sxs-lookup"><span data-stu-id="defa0-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="defa0-155">Následující příklad používá předchozí příkaz <xref:System.Data.DataSet> k naplnění s výsledky balíčku Oracle.</span><span class="sxs-lookup"><span data-stu-id="defa0-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="defa0-156">Chcete-li se vyhnout **PřetečeníException**, doporučujeme také zpracovat jakýkoli převod z typu Oracle NUMBER <xref:System.Data.DataRow>na platný typ rozhraní .NET Framework před uložením hodnoty v .</span><span class="sxs-lookup"><span data-stu-id="defa0-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="defa0-157"><xref:System.Data.Common.DataAdapter.FillError> Událost můžete použít k určení, pokud došlo k **OverflowException.**</span><span class="sxs-lookup"><span data-stu-id="defa0-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="defa0-158">Další informace o <xref:System.Data.Common.DataAdapter.FillError> události naleznete v tématu [Zpracování událostí datového adaptéru](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="defa0-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="defa0-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="defa0-159">See also</span></span>

- [<span data-ttu-id="defa0-160">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="defa0-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="defa0-161">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="defa0-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="defa0-162">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="defa0-162">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="defa0-163">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="defa0-163">ADO.NET Overview</span></span>](ado-net-overview.md)
