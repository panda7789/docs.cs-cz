---
title: Informace o chybě na řádku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 5ede6e2cd52ad55f8c35a42d137044dd1ceea400
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785954"
---
# <a name="row-error-information"></a><span data-ttu-id="ca6e2-102">Informace o chybě na řádku</span><span class="sxs-lookup"><span data-stu-id="ca6e2-102">Row Error Information</span></span>
<span data-ttu-id="ca6e2-103">Abyste se vyhnuli nutnosti reagovat na chyby řádku při úpravách <xref:System.Data.DataTable>hodnot v, můžete na řádek přidat informace o chybě pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="ca6e2-104"><xref:System.Data.DataRow> Objekt<xref:System.Data.DataRow.RowError%2A> poskytuje vlastnost na každém řádku pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="ca6e2-105">Přidání dat do vlastnosti **RowError** objektu **DataRow** nastaví <xref:System.Data.DataRow.HasErrors%2A> vlastnost **DataRow** na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="ca6e2-106">Pokud je **objekt DataRow** součástí **objektu DataTable**a vlastnost **DataRow. HasErrors** má **hodnotu true**, vlastnost **DataTable. HasErrors** má také **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="ca6e2-107">To platí i pro **datovou sadu** , ke které patří tabulka **DataTable** .</span><span class="sxs-lookup"><span data-stu-id="ca6e2-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="ca6e2-108">Při testování chyb můžete zaškrtnout vlastnost **HasErrors** a zjistit, zda byly do libovolného řádku přidány informace o chybě.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="ca6e2-109">Pokud má HasErrors **hodnotu true**, <xref:System.Data.DataTable.GetErrors%2A> můžete použít metodu **DataTable** k vrácení a prohlédnutí pouze řádků s chybami, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca6e2-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca6e2-110">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="ca6e2-111">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="ca6e2-111">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="ca6e2-112">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ca6e2-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
