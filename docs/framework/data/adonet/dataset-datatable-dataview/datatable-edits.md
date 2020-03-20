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
# <a name="datatable-edits"></a><span data-ttu-id="5fbe7-102">Úpravy datových tabulek</span><span class="sxs-lookup"><span data-stu-id="5fbe7-102">DataTable Edits</span></span>
<span data-ttu-id="5fbe7-103">Když provedete změny hodnot <xref:System.Data.DataRow>sloupců v , změny jsou okamžitě umístěny v aktuálním stavu řádku.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="5fbe7-104">Potom <xref:System.Data.DataRowState> je nastavena na **Změnit**a změny jsou <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> přijaty nebo odmítnuty pomocí metody nebo **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="5fbe7-105">**DataRow** také poskytuje tři metody, které můžete použít k pozastavení stavu řádku při jeho úpravách.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="5fbe7-106">Tyto metody <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A>jsou <xref:System.Data.DataRow.CancelEdit%2A>, a .</span><span class="sxs-lookup"><span data-stu-id="5fbe7-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="5fbe7-107">Když přímo upravujete hodnoty sloupců v **datarowu,** **datarow** spravuje hodnoty sloupců pomocí **aktuálních**, **výchozích**a **původních** verzí řádků.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="5fbe7-108">Kromě těchto verzí řádků používají metody **BeginEdit**, **EndEdit**a **CancelEdit** verzi čtvrtého řádku: **Proposed**.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="5fbe7-109">Další informace o verzích řádků naleznete v [tématu Stavy řádků a Verze řádků](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="5fbe7-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="5fbe7-110">Verze **navržený** řádek existuje během operace úprav, která začíná voláním **BeginEdit** a která končí buď pomocí **EndEdit** nebo **CancelEdit,** nebo voláním **AcceptChanges** nebo **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="5fbe7-111">Během operace úprav můžete použít logiku ověření pro jednotlivé sloupce vyhodnocením **Události ProposedValue** v **události ColumnChanged** **datatable**.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="5fbe7-112">Událost **ColumnChanged** obsahuje **dataColumnChangeEventArgs,** které uchovává odkaz na sloupec, který se mění, a na **hodnotu ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="5fbe7-113">Po vyhodnocení navrhované hodnoty ji můžete upravit nebo zrušit.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="5fbe7-114">Po ukončení úpravy se řádek přesune ze stavu **Navržený.**</span><span class="sxs-lookup"><span data-stu-id="5fbe7-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="5fbe7-115">Úpravy můžete potvrdit voláním **endeditu**nebo je můžete zrušit voláním **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="5fbe7-116">Všimněte si, že zatímco **EndEdit** potvrdí vaše úpravy, **DataSet** ve skutečnosti nepřijímá změny, dokud **AcceptChanges** je volána.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="5fbe7-117">Všimněte si také, že pokud zavoláte **AcceptChanges** před ukončením úpravy pomocí **EndEdit** nebo **CancelEdit**, úprava je ukončena a **navrhované** hodnoty řádků jsou přijaty pro **aktuální** i **původní** verze řádku.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="5fbe7-118">Stejným způsobem volání **RejectChanges** ukončí úpravy a zahodí **aktuální** a **navržený** řádek verze.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="5fbe7-119">Volání **EndEdit** nebo **CancelEdit** po volání **AcceptChanges** nebo **RejectChanges** nemá žádný vliv, protože úprava již skončila.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="5fbe7-120">Následující příklad ukazuje, jak používat **BeginEdit** s **EndEdit** a **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="5fbe7-121">Příklad také zkontroluje **Událost ProposedValue** v **události ColumnChanged** a rozhodne, zda chcete zrušit úpravy.</span><span class="sxs-lookup"><span data-stu-id="5fbe7-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5fbe7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fbe7-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="5fbe7-123">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="5fbe7-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="5fbe7-124">Zpracování událostí datové tabulky</span><span class="sxs-lookup"><span data-stu-id="5fbe7-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="5fbe7-125">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5fbe7-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
