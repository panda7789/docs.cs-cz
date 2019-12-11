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
ms.openlocfilehash: 62d105dc3c0b9aabc3699c12259e1624ac31a3a0
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960440"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="143c0-102">Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="143c0-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="143c0-103">Značka vložení v ovládacím prvku <xref:System.Windows.Forms.ListView> zobrazuje uživatele bodu, kde budou vloženy přetažené položky.</span><span class="sxs-lookup"><span data-stu-id="143c0-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="143c0-104">Když uživatel přetáhne položku do bodu mezi dvěma ostatními položkami, zobrazí se na této značce očekávané nové umístění.</span><span class="sxs-lookup"><span data-stu-id="143c0-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
 <span data-ttu-id="143c0-105">Následující obrázek ukazuje značku vložení:</span><span class="sxs-lookup"><span data-stu-id="143c0-105">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="143c0-106">![Snímek obrazovky zobrazující značku vložení ListView](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="143c0-106">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="143c0-107">Následující příklad kódu ukazuje, jak používat tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="143c0-107">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="143c0-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="143c0-108">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="143c0-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="143c0-109">Compiling the Code</span></span>  
 <span data-ttu-id="143c0-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="143c0-110">This example requires:</span></span>  
  
- <span data-ttu-id="143c0-111">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="143c0-111">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="143c0-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="143c0-112">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="143c0-113">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="143c0-113">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="143c0-114">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="143c0-114">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="143c0-115">Návod: Provádění operace přetažení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="143c0-115">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
