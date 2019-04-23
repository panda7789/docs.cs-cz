---
title: Úpravy datových tabulek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 0300ceab16d9a94bd04468f7acd105e69d13e643
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150940"
---
# <a name="datatable-edits"></a>Úpravy datových tabulek
Když provedete změny hodnot sloupce v <xref:System.Data.DataRow>, změny se okamžitě umístí v aktuálním stavu řádku. <xref:System.Data.DataRowState> Je nastaven na **změněné**, a změny budou přijímat nebo odmítat. pomocí <xref:System.Data.DataRow.AcceptChanges%2A> nebo <xref:System.Data.DataRow.RejectChanges%2A> metody **DataRow**. **DataRow** také poskytuje tři metody, které vám umožní pozastavit stavu řádku, pokud jeho úpravě. Tyto metody jsou <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, a <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Při změně hodnot sloupce v **DataRow** přímo **DataRow** spravuje hodnoty ve sloupcích pomocí **aktuální**, **výchozí**, a **Původní** verze řádků. Kromě těchto verze řádků **funkce BeginEdit**, **EndEdit –**, a **metodu CancelEdit** metody používají čtvrtý řádek verze: **Navrhované**. Další informace o verzích řádku, naleznete v tématu [stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 **Navrhované** verze řádku existuje během operace úprav, který začíná voláním **funkce BeginEdit** a, který končí buď pomocí **EndEdit –** nebo **metodu CancelEdit,**  nebo voláním **metoda AcceptChanges** nebo **RejectChanges**.  
  
 Během operace úprav, můžete použít logiku ověřování pro jednotlivé sloupce vyhodnocením **ProposedValue** v **ColumnChanged** událost **DataTable**. **ColumnChanged** událostí obsahuje **DataColumnChangeEventArgs** odkaz, který zachovat sloupec, který se mění a do **ProposedValue**. Po vyhodnocení navrhovanou hodnotu, můžete ho upravit nebo zrušit úpravy. Po ukončení úpravy řádku přesune z celkového počtu **navrhované** stavu.  
  
 Změny můžete potvrdit voláním **EndEdit –**, nebo můžete je zrušit po zavolání **metodu CancelEdit**. Všimněte si, že při **EndEdit –** potvrďte provedené úpravy **datovou sadu** skutečně nepřijímá změny do **metoda AcceptChanges** je volána. Všimněte si také, že pokud zavoláte **metoda AcceptChanges** před být ukončeny úprav s **EndEdit –** nebo **metodu CancelEdit**, skončila úpravy a **navrhované** hodnoty řádků jsou přijati pro obě **aktuální** a **původní** verze řádků. Stejným způsobem volání **RejectChanges** končí úpravy a zahodí **aktuální** a **navrhované** verze řádků. Volání **EndEdit –** nebo **metodu CancelEdit** po volání **metoda AcceptChanges** nebo **RejectChanges** nemá žádný vliv, protože již má úpravy byla ukončena.  
  
 Následující příklad ukazuje, jak používat **funkce BeginEdit** s **EndEdit –** a **metodu CancelEdit**. Příklad také kontroluje **ProposedValue** v **ColumnChanged** událostí a určuje, jestli se má zrušit úpravy.  
  
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
- [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [Zpracování událostí datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
