---
title: Vytvoření datové tabulky ze zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d45cf41-d8ae-4409-af3e-a96a7e476d85
ms.openlocfilehash: e5135aca49a63aafa3330832c54f2d28d31d60d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151348"
---
# <a name="creating-a-datatable-from-a-dataview"></a><span data-ttu-id="20781-102">Vytvoření datové tabulky ze zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="20781-102">Creating a DataTable from a DataView</span></span>
<span data-ttu-id="20781-103">Jakmile načtete data ze zdroje dat a <xref:System.Data.DataTable> naplníte je daty, můžete vrátit data seřadit, filtrovat nebo jinak omezit, aniž byste je znovu načetli.</span><span class="sxs-lookup"><span data-stu-id="20781-103">Once you have retrieved data from a data source, and have filled a <xref:System.Data.DataTable> with the data, you may want to sort, filter, or otherwise limit the returned data without retrieving it again.</span></span> <span data-ttu-id="20781-104">Třída <xref:System.Data.DataView> to umožňuje.</span><span class="sxs-lookup"><span data-stu-id="20781-104">The <xref:System.Data.DataView> class makes this possible.</span></span> <span data-ttu-id="20781-105">Kromě toho, pokud potřebujete vytvořit <xref:System.Data.DataTable> nový <xref:System.Data.DataView>z , <xref:System.Data.DataView.ToTable%2A> můžete použít metodu ke kopírování všech řádků a sloupců <xref:System.Data.DataTable>nebo podmnožinu dat do nového .</span><span class="sxs-lookup"><span data-stu-id="20781-105">In addition, if you need to create a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView>, you can use the <xref:System.Data.DataView.ToTable%2A> method to copy all the rows and columns, or a subset of the data into a new <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="20781-106">Metoda <xref:System.Data.DataView.ToTable%2A> poskytuje přetížení:</span><span class="sxs-lookup"><span data-stu-id="20781-106">The <xref:System.Data.DataView.ToTable%2A> method provides overloads to:</span></span>  
  
- <span data-ttu-id="20781-107">Vytvořte <xref:System.Data.DataTable> sloupce obsahující, které jsou podmnožinou sloupců v oblasti <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="20781-107">Create a <xref:System.Data.DataTable> containing columns that are a subset of the columns in the <xref:System.Data.DataView>.</span></span>  
  
- <span data-ttu-id="20781-108">Vytvořte, <xref:System.Data.DataTable> který obsahuje pouze <xref:System.Data.DataView>odlišné řádky od , analogicky na distinct klíčové slovo v Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="20781-108">Create a <xref:System.Data.DataTable> that includes only distinct rows from the <xref:System.Data.DataView>, analogously to the DISTINCT keyword in Transact-SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20781-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="20781-109">Example</span></span>  
 <span data-ttu-id="20781-110">Následující příklad aplikace konzoly vytvoří soubor, <xref:System.Data.DataTable> který obsahuje data z tabulky **Person.Contact** v ukázkové databázi **AdventureWorks.**</span><span class="sxs-lookup"><span data-stu-id="20781-110">The following console application example creates a <xref:System.Data.DataTable> that contains data from the **Person.Contact** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="20781-111">V dalším příkladu vytvoří seřazené a filtrované <xref:System.Data.DataView> na základě <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="20781-111">Next, the example creates a sorted and filtered <xref:System.Data.DataView> based on the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="20781-112">Po zobrazení <xref:System.Data.DataTable> obsahu a <xref:System.Data.DataView>a , v příkladu vytvoří nový <xref:System.Data.DataView.ToTable%2A> <xref:System.Data.DataTable> z <xref:System.Data.DataView> voláním metody, výběrem pouze podmnožinu dostupných sloupců.</span><span class="sxs-lookup"><span data-stu-id="20781-112">After displaying the contents of the <xref:System.Data.DataTable> and the <xref:System.Data.DataView>, the example creates a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView> by calling the <xref:System.Data.DataView.ToTable%2A> method, selecting only a subset of the available columns.</span></span> <span data-ttu-id="20781-113">Nakonec příklad zobrazí obsah nového <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="20781-113">Finally, the example displays the contents of the new <xref:System.Data.DataTable>.</span></span>  
  
```vb  
Private Sub DemonstrateDataView()  
    ' Retrieve a DataTable from the AdventureWorks sample database.  
    ' connectionString is assumed to be a valid connection string.  
    Dim adapter As New SqlDataAdapter( _  
       "SELECT FirstName, LastName, EmailAddress FROM Person.Contact WHERE FirstName LIKE 'Mich%'", connectionString)  
    Dim table As New DataTable  
  
    adapter.Fill(table)  
    Console.WriteLine("Original table name: " & table.TableName)  
    ' Print current table values.  
    PrintTableOrView(table, "Current Values in Table")  
  
    ' Now create a DataView based on the DataTable.  
    ' Sort and filter the data.  
    Dim view As DataView = table.DefaultView  
    view.Sort = "LastName, FirstName"  
    view.RowFilter = "LastName > 'M'"  
    PrintTableOrView(view, "Current Values in View")  
  
    ' Create a new DataTable based on the DataView,  
    ' requesting only two columns with distinct values  
    ' in the columns.  
    Dim newTable As DataTable = view.ToTable("UniqueLastNames", True, "FirstName", "LastName")  
    PrintTableOrView(newTable, "Table created from DataView")  
    Console.WriteLine("New table name: " & newTable.TableName)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
    End Sub  
  
Private Sub PrintTableOrView(ByVal dv As DataView, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
    Dim table As DataTable = dv.Table  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the view.  
    For Each rowView As DataRowView In dv  
        sw = New System.IO.StringWriter  
  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(rowView(col.ColumnName).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
End Sub  
  
Private Sub PrintTableOrView(ByVal table As DataTable, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the table.  
    For Each row As DataRow In table.Rows  
        sw = New System.IO.StringWriter  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(row(col).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
    End Sub  
End Module  
```  
  
```csharp  
private static void DemonstrateDataView()  
{  
// Retrieve a DataTable from the AdventureWorks sample database.  
// connectionString is assumed to be a valid connection string.  
SqlDataAdapter adapter = new SqlDataAdapter(  
    "SELECT FirstName, LastName, EmailAddress " +  
    "FROM Person.Contact WHERE FirstName LIKE 'Mich%'",
       GetConnectionString());  
DataTable table = new DataTable();  
  
adapter.Fill(table);  
Console.WriteLine("Original table name: " + table.TableName);  
// Print current table values.  
PrintTableOrView(table, "Current Values in Table");  
  
// Now create a DataView based on the DataTable.  
// Sort and filter the data.  
DataView view = table.DefaultView;  
view.Sort = "LastName, FirstName";  
view.RowFilter = "LastName > 'M'";  
PrintTableOrView(view, "Current Values in View");  
  
// Create a new DataTable based on the DataView,  
// requesting only two columns with distinct values  
// in the columns.  
DataTable newTable = view.ToTable("UniqueLastNames",  
     true, "FirstName", "LastName");  
PrintTableOrView(newTable, "Table created from DataView");  
Console.WriteLine("New table name: " + newTable.TableName);  
  
Console.WriteLine("Press any key to continue.");  
Console.ReadKey();  
}  
  
private static void PrintTableOrView(DataView dv, string label)  
{  
System.IO.StringWriter sw;  
string output;  
DataTable table = dv.Table;  
  
Console.WriteLine(label);  
  
// Loop through each row in the view.  
foreach (DataRowView rowView in dv)  
{  
    sw = new System.IO.StringWriter();  
  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(rowView[col.ColumnName].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
}  
Console.WriteLine();  
}  
  
private static void PrintTableOrView(DataTable table, string label)  
{  
System.IO.StringWriter sw;  
string output;  
  
Console.WriteLine(label);  
  
// Loop through each row in the table.  
foreach (DataRow row in table.Rows)  
{  
    sw = new System.IO.StringWriter();  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(row[col].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
} //  
Console.WriteLine();  
}  
```  
  
 <span data-ttu-id="20781-114">}</span><span class="sxs-lookup"><span data-stu-id="20781-114">}</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20781-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="20781-115">See also</span></span>

- <xref:System.Data.DataView.ToTable%2A>
- [<span data-ttu-id="20781-116">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="20781-116">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="20781-117">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="20781-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
