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
ms.openlocfilehash: f5de00fd41b24fc1a7f1ff4484c3a126e98952a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967837"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="606d5-102">Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="606d5-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="606d5-103">Značka vložení v <xref:System.Windows.Forms.ListView> ovládacím prvku zobrazí uživatele bodu, kam budou vloženy přetažené položky.</span><span class="sxs-lookup"><span data-stu-id="606d5-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="606d5-104">Když uživatel přetáhne položku do bodu mezi dvěma ostatními položkami, zobrazí se na této značce očekávané nové umístění.</span><span class="sxs-lookup"><span data-stu-id="606d5-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="606d5-105">Funkce značek vložení je k dispozici pouze [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] v případě, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> že vaše aplikace volá metodu.</span><span class="sxs-lookup"><span data-stu-id="606d5-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="606d5-106">V předchozích operačních systémech žádný kód týkající se značky vložení nemá žádný vliv a značka vložení se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="606d5-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="606d5-107">Další informace naleznete v tématu <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="606d5-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="606d5-108">Následující obrázek ukazuje značku vložení:</span><span class="sxs-lookup"><span data-stu-id="606d5-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="606d5-109">![Snímek obrazovky zobrazující značku vložení ListView](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="606d5-109">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="606d5-110">Následující příklad kódu ukazuje, jak používat tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="606d5-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="606d5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="606d5-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="606d5-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="606d5-112">Compiling the Code</span></span>  
 <span data-ttu-id="606d5-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="606d5-113">This example requires:</span></span>  
  
- <span data-ttu-id="606d5-114">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="606d5-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="606d5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="606d5-115">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="606d5-116">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="606d5-116">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="606d5-117">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="606d5-117">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="606d5-118">Návod: Provádění operace přetažení v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="606d5-118">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
