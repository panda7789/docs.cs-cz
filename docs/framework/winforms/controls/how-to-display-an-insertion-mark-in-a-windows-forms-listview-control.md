---
title: 'Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: f3dff351052eaaf70737c6410c1367ab568f6fd0
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586516"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="84e58-102">Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="84e58-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="84e58-103">Značky vložení v <xref:System.Windows.Forms.ListView> ovládací prvek zobrazuje uživatele, kteří bodu vloženy Přetahované položky.</span><span class="sxs-lookup"><span data-stu-id="84e58-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="84e58-104">Když uživatel přetáhne položku do bodu mezi dvě další položky, značky vložení ukazuje očekávané nové umístění položky.</span><span class="sxs-lookup"><span data-stu-id="84e58-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84e58-105">Označit funkce vložení dostupná pouze na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="84e58-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84e58-106">Ve starších operačních systémech jakýkoli kód týkající se značky vložení nemá žádný vliv a značky vložení nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="84e58-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="84e58-107">Další informace naleznete v tématu <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="84e58-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="84e58-108">Následující obrázek ukazuje značky vložení:</span><span class="sxs-lookup"><span data-stu-id="84e58-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="84e58-109">![Snímek obrazovky zobrazující značky vložení ListView. ](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="84e58-109">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="84e58-110">Následující příklad kódu ukazuje, jak tuto funkci používat.</span><span class="sxs-lookup"><span data-stu-id="84e58-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84e58-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="84e58-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84e58-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="84e58-112">Compiling the Code</span></span>  
 <span data-ttu-id="84e58-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="84e58-113">This example requires:</span></span>  
  
- <span data-ttu-id="84e58-114">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="84e58-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e58-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84e58-115">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="84e58-116">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="84e58-116">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="84e58-117">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="84e58-117">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="84e58-118">Návod: Operace a přetažení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84e58-118">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
