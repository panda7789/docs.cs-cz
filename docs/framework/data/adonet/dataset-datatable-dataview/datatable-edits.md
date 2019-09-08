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
# <a name="datatable-edits"></a><span data-ttu-id="f89ee-102">Úpravy datových tabulek</span><span class="sxs-lookup"><span data-stu-id="f89ee-102">DataTable Edits</span></span>
<span data-ttu-id="f89ee-103">Když provedete změny v hodnotách sloupců <xref:System.Data.DataRow>v, změny se okamžitě umístí do aktuálního stavu řádku.</span><span class="sxs-lookup"><span data-stu-id="f89ee-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="f89ee-104"><xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A>Je pak nastaveno na hodnotu změněno a změny jsou přijímány nebo odmítnuty pomocí metod nebo objektu DataRow. <xref:System.Data.DataRowState></span><span class="sxs-lookup"><span data-stu-id="f89ee-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="f89ee-105">**Objekt DataRow** také nabízí tři metody, které lze použít k pozastavení stavu řádku při jeho úpravách.</span><span class="sxs-lookup"><span data-stu-id="f89ee-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="f89ee-106">Tyto metody jsou <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>a <xref:System.Data.DataRow.CancelEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="f89ee-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="f89ee-107">Když upravujete hodnoty sloupců přímo v objektu **DataRow** , **objekt DataRow** spravuje hodnoty sloupců pomocí **aktuální**, **výchozí**a **původní** verze řádku.</span><span class="sxs-lookup"><span data-stu-id="f89ee-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="f89ee-108">Kromě těchto verzí řádků používají metody **metody BeginEdit**, **metodu EndEdit volat**a **CancelEdit** verzi čtvrtého řádku: **Navrženo**.</span><span class="sxs-lookup"><span data-stu-id="f89ee-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="f89ee-109">Další informace o verzích řádků najdete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="f89ee-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="f89ee-110">**Navrhovaná** verze řádku existuje během operace Edit, která začíná voláním **metody BeginEdit** a končí buď pomocí **metodu EndEdit volat** nebo **CancelEdit,** nebo voláním **AcceptChanges** nebo **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="f89ee-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="f89ee-111">Během operace Edit můžete použít logiku ověřování pro jednotlivé sloupce vyhodnocením **ProposedValue** v události **ColumnChanged** **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="f89ee-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="f89ee-112">Událost **ColumnChanged** obsahuje **DataColumnChangeEventArgs** , která uchovává odkaz na sloupec, který se mění a na **ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="f89ee-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="f89ee-113">Jakmile vyhodnocujete navrhovanou hodnotu, můžete ji buď změnit, nebo zrušit její úpravy.</span><span class="sxs-lookup"><span data-stu-id="f89ee-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="f89ee-114">Po ukončení úprav se řádek přesune z **navrhovaného** stavu.</span><span class="sxs-lookup"><span data-stu-id="f89ee-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="f89ee-115">Úpravy můžete potvrdit voláním **metodu EndEdit volat**, nebo je můžete zrušit voláním **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="f89ee-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="f89ee-116">Všimněte si, že i když **metodu EndEdit volat** potvrdí vaše úpravy, **datová sada** ve skutečnosti nepřijme změny, dokud nebudete volat metodu **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="f89ee-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="f89ee-117">Všimněte si také, že pokud zavoláte metodu **AcceptChanges** před ukončením úprav pomocí **metodu EndEdit volat** nebo **CancelEdit**, dokončí se úpravy a **navrhované** hodnoty řádků budou přijaty jak pro **aktuální** , tak pro **původní** verze řádků.</span><span class="sxs-lookup"><span data-stu-id="f89ee-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="f89ee-118">Stejným způsobem volání **RejectChanges** ukončí úpravu a zahodí verze **aktuálního** a **navrhovaného** řádku.</span><span class="sxs-lookup"><span data-stu-id="f89ee-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="f89ee-119">Volání **metodu EndEdit volat** nebo **CancelEdit** po volání metody **AcceptChanges** nebo **RejectChanges** nemá žádný účinek, protože úpravy již byly ukončeny.</span><span class="sxs-lookup"><span data-stu-id="f89ee-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="f89ee-120">Následující příklad ukazuje, jak používat **metody BeginEdit** s **metodu EndEdit volat** a **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="f89ee-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="f89ee-121">Příklad také zkontroluje **ProposedValue** v události **ColumnChanged** a rozhodne, zda chcete úpravu zrušit.</span><span class="sxs-lookup"><span data-stu-id="f89ee-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f89ee-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f89ee-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="f89ee-123">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="f89ee-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="f89ee-124">Zpracování událostí datové tabulky</span><span class="sxs-lookup"><span data-stu-id="f89ee-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="f89ee-125">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f89ee-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
