---
title: 'Postupy: Povolení změny pořadí položek ToolStrip za běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
ms.openlocfilehash: 44b52bf997819f090569d08eb395d8af18f61370
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745486"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="9d6d6-102">Postupy: Povolení změny pořadí položek ToolStrip za běhu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d6d6-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="9d6d6-103">Můžete uživateli povolit změnu uspořádání <xref:System.Windows.Forms.ToolStripItem> ovládacích prvků na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="9d6d6-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="9d6d6-104">Povolení změny uspořádání ToolStripItem v době běhu</span><span class="sxs-lookup"><span data-stu-id="9d6d6-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
- <span data-ttu-id="9d6d6-105">Vlastnost <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> nastavte na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="9d6d6-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="9d6d6-106">Ve výchozím nastavení je <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> `false`.</span><span class="sxs-lookup"><span data-stu-id="9d6d6-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="9d6d6-107">V době běhu uživatel drží klávesu ALT a levé tlačítko myši k přetažení <xref:System.Windows.Forms.ToolStripItem> do jiného umístění v <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="9d6d6-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9d6d6-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d6d6-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [<span data-ttu-id="9d6d6-109">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9d6d6-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="9d6d6-110">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9d6d6-110">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="9d6d6-111">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9d6d6-111">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
