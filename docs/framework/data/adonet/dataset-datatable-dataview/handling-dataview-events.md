---
title: Zpracování událostí zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 2f30a578c5233e8b86a165dd220efd45348c5042
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541091"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="12fcb-102">Zpracování událostí zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="12fcb-102">Handling DataView Events</span></span>
<span data-ttu-id="12fcb-103">Můžete použít <xref:System.Data.DataView.ListChanged> událost <xref:System.Data.DataView> k určení, jestli má aktualizované zobrazení.</span><span class="sxs-lookup"><span data-stu-id="12fcb-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="12fcb-104">Aktualizace, které vyvolávají události zahrnují přidání, odstranění nebo úprava řádků v podkladové tabulce; Přidání nebo odstranění sloupce do schématu podkladové tabulce. a změna v nadřazené nebo podřízené relace.</span><span class="sxs-lookup"><span data-stu-id="12fcb-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="12fcb-105">**ListChanged** události také vás upozorní, pokud seznam řádků se vám zobrazuje významně změnil z důvodu použití nového pořadí řazení nebo filtru.</span><span class="sxs-lookup"><span data-stu-id="12fcb-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="12fcb-106">**ListChanged** implementuje událostí **ListChangedEventHandler** delegáta z <xref:System.ComponentModel> obor názvů a přijímá jako vstup <xref:System.ComponentModel.ListChangedEventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="12fcb-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="12fcb-107">Můžete určit, jaký typ změn došlo k použití <xref:System.ComponentModel.ListChangedType> hodnota výčtu v **ListChangedType** vlastnost **ListChangedEventArgs** objektu.</span><span class="sxs-lookup"><span data-stu-id="12fcb-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="12fcb-108">Změny, které zahrnují přidání, odstranění nebo Přesun řádků, nový index řádku přidané nebo přesunut a předchozí index odstraněném řádku lze přistupovat pomocí **NewIndex** vlastnost **ListChangedEventArgs** objektu.</span><span class="sxs-lookup"><span data-stu-id="12fcb-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="12fcb-109">V případě řádku přesunutý předchozí index řádku přesunutý lze přistupovat pomocí **OldIndex** vlastnost **ListChangedEventArgs** objektu.</span><span class="sxs-lookup"><span data-stu-id="12fcb-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="12fcb-110">**Objekt DataViewManager** taky zpřístupňuje **ListChanged** události, které vás upozorní, pokud tabulky byly přidány nebo odebrány nebo pokud byla provedena změna **vztahy** kolekce základní **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="12fcb-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="12fcb-111">Následující příklad kódu ukazuje, jak přidat **ListChanged** obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="12fcb-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12fcb-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="12fcb-112">See Also</span></span>  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [<span data-ttu-id="12fcb-113">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="12fcb-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="12fcb-114">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="12fcb-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
