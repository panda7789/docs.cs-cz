---
title: 'Postupy: Povolení změny pořadí položek ToolStrip za běhu ve Windows Forms'
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
ms.openlocfilehash: 0800acc955ff8cf9efa7bc183f10d2b5cc87aac6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713710"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="fa462-102">Postupy: Povolení změny pořadí položek ToolStrip za běhu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fa462-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="fa462-103">Můžete povolit uživatelům změnit uspořádání <xref:System.Windows.Forms.ToolStripItem> ovládací prvky na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="fa462-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="fa462-104">Aby ovládací prvek ToolStripItem změny uspořádání v době běhu</span><span class="sxs-lookup"><span data-stu-id="fa462-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
-   <span data-ttu-id="fa462-105">Nastavte <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="fa462-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="fa462-106">Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> je `false`.</span><span class="sxs-lookup"><span data-stu-id="fa462-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="fa462-107">V době běhu uživatele obsahuje stisknutou klávesu ALT a levé tlačítko myši přetáhněte <xref:System.Windows.Forms.ToolStripItem> do jiného umístění v <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="fa462-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fa462-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa462-108">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [<span data-ttu-id="fa462-109">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="fa462-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="fa462-110">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="fa462-110">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="fa462-111">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="fa462-111">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
