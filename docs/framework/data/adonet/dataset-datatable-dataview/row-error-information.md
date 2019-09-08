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
# <a name="row-error-information"></a>Informace o chybě na řádku
Abyste se vyhnuli nutnosti reagovat na chyby řádku při úpravách <xref:System.Data.DataTable>hodnot v, můžete na řádek přidat informace o chybě pro pozdější použití. <xref:System.Data.DataRow> Objekt<xref:System.Data.DataRow.RowError%2A> poskytuje vlastnost na každém řádku pro tento účel. Přidání dat do vlastnosti **RowError** objektu **DataRow** nastaví <xref:System.Data.DataRow.HasErrors%2A> vlastnost **DataRow** na **hodnotu true**. Pokud je **objekt DataRow** součástí **objektu DataTable**a vlastnost **DataRow. HasErrors** má **hodnotu true**, vlastnost **DataTable. HasErrors** má také **hodnotu true**. To platí i pro **datovou sadu** , ke které patří tabulka **DataTable** . Při testování chyb můžete zaškrtnout vlastnost **HasErrors** a zjistit, zda byly do libovolného řádku přidány informace o chybě. Pokud má HasErrors **hodnotu true**, <xref:System.Data.DataTable.GetErrors%2A> můžete použít metodu **DataTable** k vrácení a prohlédnutí pouze řádků s chybami, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [Přehled ADO.NET](../ado-net-overview.md)
