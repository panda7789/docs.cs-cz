---
title: "Úpravy DataTable"
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
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d33bd8900c48222142a46ed2c5bd64412d2eaab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-edits"></a><span data-ttu-id="307a1-102">Úpravy DataTable</span><span class="sxs-lookup"><span data-stu-id="307a1-102">DataTable Edits</span></span>
<span data-ttu-id="307a1-103">Když provedete změny hodnot sloupce v <xref:System.Data.DataRow>, změny jsou okamžitě umístěny v aktuálním stavu řádku.</span><span class="sxs-lookup"><span data-stu-id="307a1-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="307a1-104"><xref:System.Data.DataRowState> Pak nastavena na **změněné**, a změny jsou přijetí nebo odmítnutí pomocí <xref:System.Data.DataRow.AcceptChanges%2A> nebo <xref:System.Data.DataRow.RejectChanges%2A> metody **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="307a1-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="307a1-105">**DataRow** také poskytuje tři metody, které můžete pozastavit stav řádek během úprav.</span><span class="sxs-lookup"><span data-stu-id="307a1-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="307a1-106">Tyto metody jsou <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, a <xref:System.Data.DataRow.CancelEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="307a1-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="307a1-107">Při změně hodnoty ve sloupcích v **DataRow** přímo **DataRow** spravuje hodnoty ve sloupcích pomocí **aktuální**, **výchozí**, a **Původní** řádek verze.</span><span class="sxs-lookup"><span data-stu-id="307a1-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="307a1-108">Kromě těchto verzí řádek **BeginEdit**, **EndEdit –**, a **CancelEdit** metody použití Čtvrtá verze řádku: **navržený**.</span><span class="sxs-lookup"><span data-stu-id="307a1-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="307a1-109">Další informace o verzích řádek najdete v tématu [stavy řádků a verze řádku](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="307a1-109">For more information about row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="307a1-110">**Navržený** verze řádku existuje během operace úpravy, která začíná voláním **BeginEdit** a který končí buď pomocí **EndEdit –** nebo **CancelEdit,**  nebo voláním **metoda AcceptChanges** nebo **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="307a1-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="307a1-111">Během operace úpravy, můžete použít logiku ověření pro jednotlivé sloupce vyhodnocením **ProposedValue** v **ColumnChanged** události **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="307a1-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="307a1-112">**ColumnChanged** událostí obsahuje **DataColumnChangeEventArgs** pro sloupec, který se mění a která odkaz zachovat **ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="307a1-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="307a1-113">Po ohodnocení navrhované hodnoty, můžete ho změnit nebo zrušit úpravy.</span><span class="sxs-lookup"><span data-stu-id="307a1-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="307a1-114">Po ukončení úpravy řádek přesune mimo **navržený** stavu.</span><span class="sxs-lookup"><span data-stu-id="307a1-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="307a1-115">Úpravy si můžete ověřit pomocí volání **EndEdit –**, nebo je můžete zrušit voláním **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="307a1-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="307a1-116">Všimněte si, že chvíli **EndEdit –** potvrďte provedené úpravy **datovou sadu** ve skutečnosti nepřijímá změny dokud **metoda AcceptChanges** je volána.</span><span class="sxs-lookup"><span data-stu-id="307a1-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="307a1-117">Poznámka: Když zavoláte **metoda AcceptChanges** před být ukončeny upravit s **EndEdit –** nebo **CancelEdit**, je zakončeno úpravy a **navržený** jsou podmínky přijaty ve obě hodnoty řádků **aktuální** a **původní** řádek verze.</span><span class="sxs-lookup"><span data-stu-id="307a1-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="307a1-118">Stejným způsobem volání **RejectChanges** končí úpravy a zahodí **aktuální** a **navržený** řádek verze.</span><span class="sxs-lookup"><span data-stu-id="307a1-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="307a1-119">Volání metody **EndEdit –** nebo **CancelEdit** po volání **metoda AcceptChanges** nebo **RejectChanges** nemá žádný vliv, protože již bylo úpravy byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="307a1-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="307a1-120">Následující příklad ukazuje, jak používat **BeginEdit** s **EndEdit –** a **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="307a1-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="307a1-121">Příklad také kontroluje **ProposedValue** v **ColumnChanged** událostí a určuje, jestli se má zrušit úpravy.</span><span class="sxs-lookup"><span data-stu-id="307a1-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="307a1-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="307a1-122">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [<span data-ttu-id="307a1-123">Manipulace s daty v DataTable</span><span class="sxs-lookup"><span data-stu-id="307a1-123">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="307a1-124">Zpracování událostí DataTable</span><span class="sxs-lookup"><span data-stu-id="307a1-124">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="307a1-125">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="307a1-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
