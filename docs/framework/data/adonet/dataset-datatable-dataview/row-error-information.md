---
title: Informace o chybě na řádku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 89889c5543e6518046bb59b59646ecba715f5e03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152721"
---
# <a name="row-error-information"></a><span data-ttu-id="d4751-102">Informace o chybě na řádku</span><span class="sxs-lookup"><span data-stu-id="d4751-102">Row Error Information</span></span>
<span data-ttu-id="d4751-103">Abyste se vyhnuli nutnosti reakce na chyby řádek při úpravách hodnoty v <xref:System.Data.DataTable>, můžete přidat informace o chybě na řádku pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="d4751-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="d4751-104"><xref:System.Data.DataRow> Objekt, který poskytuje <xref:System.Data.DataRow.RowError%2A> vlastnost pro každý řádek pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="d4751-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="d4751-105">Přidání dat do **RowError** vlastnost **DataRow** nastaví <xref:System.Data.DataRow.HasErrors%2A> vlastnost **DataRow** k **true**.</span><span class="sxs-lookup"><span data-stu-id="d4751-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="d4751-106">Pokud **DataRow** je součástí **DataTable**, a **DataRow.HasErrors** je **true**, **DataTable.HasErrors** vlastnost je také **true**.</span><span class="sxs-lookup"><span data-stu-id="d4751-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="d4751-107">To platí i pro **datovou sadu** ke kterému **DataTable** patří.</span><span class="sxs-lookup"><span data-stu-id="d4751-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="d4751-108">Při testování pro nalezení chyb, můžete zkontrolovat **HasErrors** a určí, pokud informace o chybě se přidala do všech řádků.</span><span class="sxs-lookup"><span data-stu-id="d4751-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="d4751-109">Pokud **HasErrors** je **true**, můžete použít <xref:System.Data.DataTable.GetErrors%2A> metodu **DataTable** se vraťte a prozkoumat pouze řádky s chybami, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d4751-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4751-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4751-110">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="d4751-111">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="d4751-111">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="d4751-112">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="d4751-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
