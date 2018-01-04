---
title: "Postupy: Výběr položky v ovládacím prvku Windows Forms ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef672dc909717ba979d81bd98510dad6419583a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="a0b79-102">Postupy: Výběr položky v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="a0b79-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="a0b79-103">Tento příklad ukazuje, jak prostřednictvím kódu programu vyberte položku v systému Windows Forms <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a0b79-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="a0b79-104">Výběrem položky prostřednictvím kódu programu automaticky nezmění zaměření <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a0b79-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="a0b79-105">Z tohoto důvodu obvykle také můžete nastavit položku jako zaměřuje při výběru položky.</span><span class="sxs-lookup"><span data-stu-id="a0b79-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0b79-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0b79-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0b79-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a0b79-107">Compiling the Code</span></span>  
 <span data-ttu-id="a0b79-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a0b79-108">This example requires:</span></span>  
  
-   <span data-ttu-id="a0b79-109">A <xref:System.Windows.Forms.ListView> ovládací prvek s názvem `listView1` obsahující alespoň jednu položku.</span><span class="sxs-lookup"><span data-stu-id="a0b79-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
-   <span data-ttu-id="a0b79-110">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="a0b79-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b79-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0b79-111">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
