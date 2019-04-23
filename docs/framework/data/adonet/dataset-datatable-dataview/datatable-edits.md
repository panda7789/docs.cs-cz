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
# <a name="datatable-edits"></a><span data-ttu-id="ac836-102">Úpravy datových tabulek</span><span class="sxs-lookup"><span data-stu-id="ac836-102">DataTable Edits</span></span>
<span data-ttu-id="ac836-103">Když provedete změny hodnot sloupce v <xref:System.Data.DataRow>, změny se okamžitě umístí v aktuálním stavu řádku.</span><span class="sxs-lookup"><span data-stu-id="ac836-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="ac836-104"><xref:System.Data.DataRowState> Je nastaven na **změněné**, a změny budou přijímat nebo odmítat. pomocí <xref:System.Data.DataRow.AcceptChanges%2A> nebo <xref:System.Data.DataRow.RejectChanges%2A> metody **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="ac836-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="ac836-105">**DataRow** také poskytuje tři metody, které vám umožní pozastavit stavu řádku, pokud jeho úpravě.</span><span class="sxs-lookup"><span data-stu-id="ac836-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="ac836-106">Tyto metody jsou <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, a <xref:System.Data.DataRow.CancelEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac836-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="ac836-107">Při změně hodnot sloupce v **DataRow** přímo **DataRow** spravuje hodnoty ve sloupcích pomocí **aktuální**, **výchozí**, a **Původní** verze řádků.</span><span class="sxs-lookup"><span data-stu-id="ac836-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="ac836-108">Kromě těchto verze řádků **funkce BeginEdit**, **EndEdit –**, a **metodu CancelEdit** metody používají čtvrtý řádek verze: **Navrhované**.</span><span class="sxs-lookup"><span data-stu-id="ac836-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="ac836-109">Další informace o verzích řádku, naleznete v tématu [stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="ac836-109">For more information about row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="ac836-110">**Navrhované** verze řádku existuje během operace úprav, který začíná voláním **funkce BeginEdit** a, který končí buď pomocí **EndEdit –** nebo **metodu CancelEdit,**  nebo voláním **metoda AcceptChanges** nebo **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="ac836-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="ac836-111">Během operace úprav, můžete použít logiku ověřování pro jednotlivé sloupce vyhodnocením **ProposedValue** v **ColumnChanged** událost **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="ac836-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="ac836-112">**ColumnChanged** událostí obsahuje **DataColumnChangeEventArgs** odkaz, který zachovat sloupec, který se mění a do **ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="ac836-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="ac836-113">Po vyhodnocení navrhovanou hodnotu, můžete ho upravit nebo zrušit úpravy.</span><span class="sxs-lookup"><span data-stu-id="ac836-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="ac836-114">Po ukončení úpravy řádku přesune z celkového počtu **navrhované** stavu.</span><span class="sxs-lookup"><span data-stu-id="ac836-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="ac836-115">Změny můžete potvrdit voláním **EndEdit –**, nebo můžete je zrušit po zavolání **metodu CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="ac836-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="ac836-116">Všimněte si, že při **EndEdit –** potvrďte provedené úpravy **datovou sadu** skutečně nepřijímá změny do **metoda AcceptChanges** je volána.</span><span class="sxs-lookup"><span data-stu-id="ac836-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="ac836-117">Všimněte si také, že pokud zavoláte **metoda AcceptChanges** před být ukončeny úprav s **EndEdit –** nebo **metodu CancelEdit**, skončila úpravy a **navrhované** hodnoty řádků jsou přijati pro obě **aktuální** a **původní** verze řádků.</span><span class="sxs-lookup"><span data-stu-id="ac836-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="ac836-118">Stejným způsobem volání **RejectChanges** končí úpravy a zahodí **aktuální** a **navrhované** verze řádků.</span><span class="sxs-lookup"><span data-stu-id="ac836-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="ac836-119">Volání **EndEdit –** nebo **metodu CancelEdit** po volání **metoda AcceptChanges** nebo **RejectChanges** nemá žádný vliv, protože již má úpravy byla ukončena.</span><span class="sxs-lookup"><span data-stu-id="ac836-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="ac836-120">Následující příklad ukazuje, jak používat **funkce BeginEdit** s **EndEdit –** a **metodu CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="ac836-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="ac836-121">Příklad také kontroluje **ProposedValue** v **ColumnChanged** událostí a určuje, jestli se má zrušit úpravy.</span><span class="sxs-lookup"><span data-stu-id="ac836-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac836-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac836-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="ac836-123">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="ac836-123">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="ac836-124">Zpracování událostí datové tabulky</span><span class="sxs-lookup"><span data-stu-id="ac836-124">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="ac836-125">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ac836-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
