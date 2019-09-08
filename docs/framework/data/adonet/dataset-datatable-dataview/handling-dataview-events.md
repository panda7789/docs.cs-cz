---
title: Zpracování událostí zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: c36c68b0375e7d03aac36de7d02b2c9579ea9316
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784597"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="7f722-102">Zpracování událostí zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="7f722-102">Handling DataView Events</span></span>
<span data-ttu-id="7f722-103">Můžete použít <xref:System.Data.DataView.ListChanged> událost <xref:System.Data.DataView> k určení, zda bylo zobrazení aktualizováno.</span><span class="sxs-lookup"><span data-stu-id="7f722-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="7f722-104">Aktualizace, které vyvolávají událost, zahrnují přidání, odstranění nebo úpravu řádku v podkladové tabulce; Přidání nebo odstranění sloupce ve schématu podkladové tabulky; a změna v relaci nadřazeného nebo podřízeného vztahu.</span><span class="sxs-lookup"><span data-stu-id="7f722-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="7f722-105">Událost **ListChanged** vás také upozorní, pokud se seznam zobrazených řádků významně změnil v důsledku použití nového pořadí řazení nebo filtru.</span><span class="sxs-lookup"><span data-stu-id="7f722-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="7f722-106">Událost **ListChanged** implementuje <xref:System.ComponentModel> delegáta **ListChangedEventHandler** <xref:System.ComponentModel.ListChangedEventArgs> oboru názvů a přijímá jako vstup objekt.</span><span class="sxs-lookup"><span data-stu-id="7f722-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="7f722-107">Můžete určit, jaký typ změny došlo, pomocí <xref:System.ComponentModel.ListChangedType> hodnoty výčtu ve vlastnosti **ListChangedType** objektu **ListChangedEventArgs** .</span><span class="sxs-lookup"><span data-stu-id="7f722-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="7f722-108">Pro změny, které zahrnují přidání, odstranění nebo přesunutí řádků, je k novému indexu přidaných nebo přesunutých řádků a k předchozímu indexu odstraněného řádku možné přistupovat pomocí vlastnosti **NewIndex** objektu **ListChangedEventArgs** .</span><span class="sxs-lookup"><span data-stu-id="7f722-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="7f722-109">V případě přesunutého řádku je k předchozímu indexu přesunutého řádku možné přistupovat pomocí vlastnosti **OldIndex** objektu **ListChangedEventArgs** .</span><span class="sxs-lookup"><span data-stu-id="7f722-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="7f722-110">Objekt **DataViewManager** také zpřístupňuje událost **ListChanged** , která vás upozorní, pokud byla tabulka přidána nebo odebrána, nebo pokud byla provedena změna v kolekci **Relations** podkladové **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="7f722-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="7f722-111">Následující příklad kódu ukazuje, jak přidat obslužnou rutinu události **ListChanged** .</span><span class="sxs-lookup"><span data-stu-id="7f722-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f722-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f722-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="7f722-113">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="7f722-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="7f722-114">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7f722-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
