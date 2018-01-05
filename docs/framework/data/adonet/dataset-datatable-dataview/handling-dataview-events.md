---
title: "Zpracování událostí zobrazení dat"
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
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1f12dc41421090615e640fac4cc7bfb0fa08bb00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="handling-dataview-events"></a><span data-ttu-id="12ce9-102">Zpracování událostí zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="12ce9-102">Handling DataView Events</span></span>
<span data-ttu-id="12ce9-103">Můžete použít <xref:System.Data.DataView.ListChanged> události <xref:System.Data.DataView> k určení, zda byl aktualizován zobrazení.</span><span class="sxs-lookup"><span data-stu-id="12ce9-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="12ce9-104">Aktualizace, které vyvolání události zahrnují přidání, odstranění nebo úprava řádek v podkladové tabulce; Přidání nebo odstranění sloupce schématu základní tabulky; a změnu ve vztahu nadřazené nebo podřízené.</span><span class="sxs-lookup"><span data-stu-id="12ce9-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="12ce9-105">**ListChanged** událostí taky upozorní, zda seznam řádků prohlížíte významně změnil z důvodu aplikace nové pořadí řazení nebo filtru.</span><span class="sxs-lookup"><span data-stu-id="12ce9-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="12ce9-106">**ListChanged** implementuje událostí **ListChangedEventHandler** delegovat z <xref:System.ComponentModel> obor názvů a přijímá jako vstup <xref:System.ComponentModel.ListChangedEventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="12ce9-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="12ce9-107">Můžete určit, jaký typ změny došlo k použití <xref:System.ComponentModel.ListChangedType> hodnota výčtu v **ListChangedType** vlastnost **ListChangedEventArgs** objektu.</span><span class="sxs-lookup"><span data-stu-id="12ce9-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="12ce9-108">Změny, které zahrnují přidání, odstranění nebo přesunutí řádků, nový index řádku přidané nebo přesunutý a předchozí index odstraněné řádku lze přistupovat pomocí **NewIndex** vlastnost **ListChangedEventArgs** objektu.</span><span class="sxs-lookup"><span data-stu-id="12ce9-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="12ce9-109">V případě přesunutý řádek, předchozí index přesunutý řádku lze přistupovat pomocí **OldIndex** vlastnost **ListChangedEventArgs** objektu.</span><span class="sxs-lookup"><span data-stu-id="12ce9-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="12ce9-110">**DataViewManager** taky zpřístupňuje **ListChanged** události pro upozornění, pokud tabulka byl přidán nebo odebrán, nebo pokud ke změně k **vztahů** kolekce základní **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="12ce9-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="12ce9-111">Následující příklad kódu ukazuje, jak přidat **ListChanged** obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="12ce9-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new   
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,   
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="12ce9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="12ce9-112">See Also</span></span>  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [<span data-ttu-id="12ce9-113">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="12ce9-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="12ce9-114">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="12ce9-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
