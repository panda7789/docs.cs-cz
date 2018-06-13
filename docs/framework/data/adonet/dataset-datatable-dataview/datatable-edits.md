---
title: Úpravy DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: b806e642a5cce6a55ff0dcecc9b018f3ee78bad8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758617"
---
# <a name="datatable-edits"></a>Úpravy DataTable
Když provedete změny hodnot sloupce v <xref:System.Data.DataRow>, změny jsou okamžitě umístěny v aktuálním stavu řádku. <xref:System.Data.DataRowState> Pak nastavena na **změněné**, a změny jsou přijetí nebo odmítnutí pomocí <xref:System.Data.DataRow.AcceptChanges%2A> nebo <xref:System.Data.DataRow.RejectChanges%2A> metody **DataRow**. **DataRow** také poskytuje tři metody, které můžete pozastavit stav řádek během úprav. Tyto metody jsou <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, a <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Při změně hodnoty ve sloupcích v **DataRow** přímo **DataRow** spravuje hodnoty ve sloupcích pomocí **aktuální**, **výchozí**, a **Původní** řádek verze. Kromě těchto verzí řádek **BeginEdit**, **EndEdit –**, a **CancelEdit** metody použití Čtvrtá verze řádku: **navržený**. Další informace o verzích řádek najdete v tématu [stavy řádků a verze řádku](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 **Navržený** verze řádku existuje během operace úpravy, která začíná voláním **BeginEdit** a který končí buď pomocí **EndEdit –** nebo **CancelEdit,**  nebo voláním **metoda AcceptChanges** nebo **RejectChanges**.  
  
 Během operace úpravy, můžete použít logiku ověření pro jednotlivé sloupce vyhodnocením **ProposedValue** v **ColumnChanged** události **DataTable**. **ColumnChanged** událostí obsahuje **DataColumnChangeEventArgs** pro sloupec, který se mění a která odkaz zachovat **ProposedValue**. Po ohodnocení navrhované hodnoty, můžete ho změnit nebo zrušit úpravy. Po ukončení úpravy řádek přesune mimo **navržený** stavu.  
  
 Úpravy si můžete ověřit pomocí volání **EndEdit –**, nebo je můžete zrušit voláním **CancelEdit**. Všimněte si, že chvíli **EndEdit –** potvrďte provedené úpravy **datovou sadu** ve skutečnosti nepřijímá změny dokud **metoda AcceptChanges** je volána. Poznámka: Když zavoláte **metoda AcceptChanges** před být ukončeny upravit s **EndEdit –** nebo **CancelEdit**, je zakončeno úpravy a **navržený** jsou podmínky přijaty ve obě hodnoty řádků **aktuální** a **původní** řádek verze. Stejným způsobem volání **RejectChanges** končí úpravy a zahodí **aktuální** a **navržený** řádek verze. Volání metody **EndEdit –** nebo **CancelEdit** po volání **metoda AcceptChanges** nebo **RejectChanges** nemá žádný vliv, protože již bylo úpravy byl ukončen.  
  
 Následující příklad ukazuje, jak používat **BeginEdit** s **EndEdit –** a **CancelEdit**. Příklad také kontroluje **ProposedValue** v **ColumnChanged** událostí a určuje, jestli se má zrušit úpravy.  
  
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
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Zpracování událostí datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
