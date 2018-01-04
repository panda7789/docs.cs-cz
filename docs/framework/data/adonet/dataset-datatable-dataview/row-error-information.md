---
title: "Informace o chybě řádek"
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
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8600e7d1d14de9474bf3f9cfadb25e06f52b0b1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="row-error-information"></a><span data-ttu-id="d4483-102">Informace o chybě řádek</span><span class="sxs-lookup"><span data-stu-id="d4483-102">Row Error Information</span></span>
<span data-ttu-id="d4483-103">Abyste se vyhnuli nutnosti reagovat na řádek chyby při úpravě hodnoty v <xref:System.Data.DataTable>, informace o chybě můžete přidat na řádek pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="d4483-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="d4483-104"><xref:System.Data.DataRow> Objekt poskytuje <xref:System.Data.DataRow.RowError%2A> vlastnost na každý řádek pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="d4483-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="d4483-105">Přidání dat do **RowError** vlastnost **DataRow** nastaví <xref:System.Data.DataRow.HasErrors%2A> vlastnost **DataRow** k **true**.</span><span class="sxs-lookup"><span data-stu-id="d4483-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="d4483-106">Pokud **DataRow** je součástí **DataTable**, a **DataRow.HasErrors** je **true**, **DataTable.HasErrors** vlastnost je také **true**.</span><span class="sxs-lookup"><span data-stu-id="d4483-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="d4483-107">To platí také pro **datovou sadu** ke kterému **DataTable** patří.</span><span class="sxs-lookup"><span data-stu-id="d4483-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="d4483-108">Při testování pro nalezení chyb, můžete zkontrolovat **HasErrors** vlastnosti k určení, zda informace o chybě byl přidán k žádnému z řádků.</span><span class="sxs-lookup"><span data-stu-id="d4483-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="d4483-109">Pokud **HasErrors** je **true**, můžete použít <xref:System.Data.DataTable.GetErrors%2A> metodu **DataTable** a vrátit pouze sloupce s chybami, zkontrolujte, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d4483-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4483-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4483-110">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="d4483-111">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="d4483-111">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="d4483-112">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="d4483-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
