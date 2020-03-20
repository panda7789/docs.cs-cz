---
title: Úpravy datových tabulek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 9e8c4204b51121b147fc7614066d9b849a687574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151257"
---
# <a name="datatable-edits"></a>Úpravy datových tabulek
Když provedete změny hodnot <xref:System.Data.DataRow>sloupců v , změny jsou okamžitě umístěny v aktuálním stavu řádku. Potom <xref:System.Data.DataRowState> je nastavena na **Změnit**a změny jsou <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> přijaty nebo odmítnuty pomocí metody nebo **DataRow**. **DataRow** také poskytuje tři metody, které můžete použít k pozastavení stavu řádku při jeho úpravách. Tyto metody <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A>jsou <xref:System.Data.DataRow.CancelEdit%2A>, a .  
  
 Když přímo upravujete hodnoty sloupců v **datarowu,** **datarow** spravuje hodnoty sloupců pomocí **aktuálních**, **výchozích**a **původních** verzí řádků. Kromě těchto verzí řádků používají metody **BeginEdit**, **EndEdit**a **CancelEdit** verzi čtvrtého řádku: **Proposed**. Další informace o verzích řádků naleznete v [tématu Stavy řádků a Verze řádků](row-states-and-row-versions.md).  
  
 Verze **navržený** řádek existuje během operace úprav, která začíná voláním **BeginEdit** a která končí buď pomocí **EndEdit** nebo **CancelEdit,** nebo voláním **AcceptChanges** nebo **RejectChanges**.  
  
 Během operace úprav můžete použít logiku ověření pro jednotlivé sloupce vyhodnocením **Události ProposedValue** v **události ColumnChanged** **datatable**. Událost **ColumnChanged** obsahuje **dataColumnChangeEventArgs,** které uchovává odkaz na sloupec, který se mění, a na **hodnotu ProposedValue**. Po vyhodnocení navrhované hodnoty ji můžete upravit nebo zrušit. Po ukončení úpravy se řádek přesune ze stavu **Navržený.**  
  
 Úpravy můžete potvrdit voláním **endeditu**nebo je můžete zrušit voláním **CancelEdit**. Všimněte si, že zatímco **EndEdit** potvrdí vaše úpravy, **DataSet** ve skutečnosti nepřijímá změny, dokud **AcceptChanges** je volána. Všimněte si také, že pokud zavoláte **AcceptChanges** před ukončením úpravy pomocí **EndEdit** nebo **CancelEdit**, úprava je ukončena a **navrhované** hodnoty řádků jsou přijaty pro **aktuální** i **původní** verze řádku. Stejným způsobem volání **RejectChanges** ukončí úpravy a zahodí **aktuální** a **navržený** řádek verze. Volání **EndEdit** nebo **CancelEdit** po volání **AcceptChanges** nebo **RejectChanges** nemá žádný vliv, protože úprava již skončila.  
  
 Následující příklad ukazuje, jak používat **BeginEdit** s **EndEdit** a **CancelEdit**. Příklad také zkontroluje **Událost ProposedValue** v **události ColumnChanged** a rozhodne, zda chcete zrušit úpravy.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [Zpracování událostí datové tabulky](handling-datatable-events.md)
- [Přehled ADO.NET](../ado-net-overview.md)
