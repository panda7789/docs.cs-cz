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
ms.openlocfilehash: daff9d6d351db514d552225853f977775f8e3204
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941437"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="4b1bd-102">Postupy: Povolení změny pořadí položek ToolStrip za běhu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b1bd-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="4b1bd-103">Můžete povolit uživatelům změnit uspořádání <xref:System.Windows.Forms.ToolStripItem> ovládací prvky na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="4b1bd-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="4b1bd-104">Aby ovládací prvek ToolStripItem změny uspořádání v době běhu</span><span class="sxs-lookup"><span data-stu-id="4b1bd-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
- <span data-ttu-id="4b1bd-105">Nastavte <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="4b1bd-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="4b1bd-106">Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> je `false`.</span><span class="sxs-lookup"><span data-stu-id="4b1bd-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="4b1bd-107">V době běhu uživatele obsahuje stisknutou klávesu ALT a levé tlačítko myši přetáhněte <xref:System.Windows.Forms.ToolStripItem> do jiného umístění v <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="4b1bd-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4b1bd-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b1bd-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [<span data-ttu-id="4b1bd-109">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4b1bd-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="4b1bd-110">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4b1bd-110">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="4b1bd-111">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4b1bd-111">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
