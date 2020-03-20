---
title: Zpracování událostí zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b625fad846c4c6cf008843bff1f6b0eabe0e1de4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151101"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="6b3c3-102">Zpracování událostí zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="6b3c3-102">Handling DataView Events</span></span>
<span data-ttu-id="6b3c3-103">Událost <xref:System.Data.DataView.ListChanged> zobrazení můžete použít <xref:System.Data.DataView> k určení, zda bylo zobrazení aktualizováno.</span><span class="sxs-lookup"><span data-stu-id="6b3c3-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="6b3c3-104">Aktualizace, které vyvolávají událost patří přidání, odstranění nebo úprava řádku v podkladové tabulce; přidání nebo odstranění sloupce do schématu podkladové tabulky; a změna v nadřazeném nebo podřízeném vztahu.</span><span class="sxs-lookup"><span data-stu-id="6b3c3-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="6b3c3-105">Událost **ListChanged** vás také upozorní, pokud se seznam řádků, které prohlížíte, výrazně změnil z důvodu použití nového pořadí řazení nebo filtru.</span><span class="sxs-lookup"><span data-stu-id="6b3c3-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="6b3c3-106">Událost **ListChanged** implementuje delegáta oboru <xref:System.ComponentModel> názvů **ListChangedEventHandler** <xref:System.ComponentModel.ListChangedEventArgs> a bere jako vstupní objekt.</span><span class="sxs-lookup"><span data-stu-id="6b3c3-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="6b3c3-107">Můžete určit, jaký typ změny <xref:System.ComponentModel.ListChangedType> došlo pomocí hodnoty výčtu v **ListChangedType** vlastnost **í ListChangedEventArgs** objektu.</span><span class="sxs-lookup"><span data-stu-id="6b3c3-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="6b3c3-108">Pro změny, které zahrnují přidání, odstranění nebo přesunutí řádků, nový index přidaného nebo přesunutého řádku a předchozí index odstraněného řádku lze přistupovat pomocí **Vlastnost NewIndex** objektu **ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="6b3c3-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="6b3c3-109">V případě přesunutého řádku lze získat přístup k předchozímu indexu přesunutého řádku pomocí vlastnosti **OldIndex** objektu **ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="6b3c3-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="6b3c3-110">**DataViewManager** také zveřejňuje **ListChanged** událost upozornit, pokud tabulka byla přidána nebo odebrána, nebo pokud byla provedena změna **kolekce vztahy** podkladové **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="6b3c3-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="6b3c3-111">Následující příklad kódu ukazuje, jak přidat obslužnou rutinu události **ListChanged.**</span><span class="sxs-lookup"><span data-stu-id="6b3c3-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b3c3-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b3c3-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="6b3c3-113">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="6b3c3-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="6b3c3-114">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6b3c3-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
