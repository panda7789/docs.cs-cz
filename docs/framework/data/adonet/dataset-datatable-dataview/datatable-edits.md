---
title: Úpravy datových tabulek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 689a297eb5368d35c2e7dd034426edbe665e7ed2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785382"
---
# <a name="datatable-edits"></a>Úpravy datových tabulek
Když provedete změny v hodnotách sloupců <xref:System.Data.DataRow>v, změny se okamžitě umístí do aktuálního stavu řádku. <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A>Je pak nastaveno na hodnotu změněno a změny jsou přijímány nebo odmítnuty pomocí metod nebo objektu DataRow. <xref:System.Data.DataRowState> **Objekt DataRow** také nabízí tři metody, které lze použít k pozastavení stavu řádku při jeho úpravách. Tyto metody jsou <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>a <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Když upravujete hodnoty sloupců přímo v objektu **DataRow** , **objekt DataRow** spravuje hodnoty sloupců pomocí **aktuální**, **výchozí**a **původní** verze řádku. Kromě těchto verzí řádků používají metody **metody BeginEdit**, **metodu EndEdit volat**a **CancelEdit** verzi čtvrtého řádku: **Navrženo**. Další informace o verzích řádků najdete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).  
  
 **Navrhovaná** verze řádku existuje během operace Edit, která začíná voláním **metody BeginEdit** a končí buď pomocí **metodu EndEdit volat** nebo **CancelEdit,** nebo voláním **AcceptChanges** nebo **RejectChanges**.  
  
 Během operace Edit můžete použít logiku ověřování pro jednotlivé sloupce vyhodnocením **ProposedValue** v události **ColumnChanged** **objektu DataTable**. Událost **ColumnChanged** obsahuje **DataColumnChangeEventArgs** , která uchovává odkaz na sloupec, který se mění a na **ProposedValue**. Jakmile vyhodnocujete navrhovanou hodnotu, můžete ji buď změnit, nebo zrušit její úpravy. Po ukončení úprav se řádek přesune z **navrhovaného** stavu.  
  
 Úpravy můžete potvrdit voláním **metodu EndEdit volat**, nebo je můžete zrušit voláním **CancelEdit**. Všimněte si, že i když **metodu EndEdit volat** potvrdí vaše úpravy, **datová sada** ve skutečnosti nepřijme změny, dokud nebudete volat metodu **AcceptChanges** . Všimněte si také, že pokud zavoláte metodu **AcceptChanges** před ukončením úprav pomocí **metodu EndEdit volat** nebo **CancelEdit**, dokončí se úpravy a **navrhované** hodnoty řádků budou přijaty jak pro **aktuální** , tak pro **původní** verze řádků. Stejným způsobem volání **RejectChanges** ukončí úpravu a zahodí verze **aktuálního** a **navrhovaného** řádku. Volání **metodu EndEdit volat** nebo **CancelEdit** po volání metody **AcceptChanges** nebo **RejectChanges** nemá žádný účinek, protože úpravy již byly ukončeny.  
  
 Následující příklad ukazuje, jak používat **metody BeginEdit** s **metodu EndEdit volat** a **CancelEdit**. Příklad také zkontroluje **ProposedValue** v události **ColumnChanged** a rozhodne, zda chcete úpravu zrušit.  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""       
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=   
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";       
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);    
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [Zpracování událostí datové tabulky](handling-datatable-events.md)
- [Přehled ADO.NET](../ado-net-overview.md)
