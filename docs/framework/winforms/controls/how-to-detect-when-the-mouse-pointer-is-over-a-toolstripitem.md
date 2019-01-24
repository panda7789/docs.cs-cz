---
title: 'Postupy: Rozpoznat, kdy je ukazatel myši nad ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 20fbc91773f431fc68f606f8aa9f24f4c0cc06bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539594"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="cfc4c-102">Postupy: Rozpoznat, kdy je ukazatel myši nad ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="cfc4c-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="cfc4c-103">Použijte následující postup k zjištění umístění ukazatele myši nad <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="cfc4c-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="cfc4c-104">Chcete-li zjistit, kdy je ukazatel myši nad ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="cfc4c-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
-   <span data-ttu-id="cfc4c-105">Použití <xref:System.Windows.Forms.ToolStripItem.Selected%2A> vlastnosti pro položky, ve kterém <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> je `true`.</span><span class="sxs-lookup"><span data-stu-id="cfc4c-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="cfc4c-106">To zabrání by bylo nutné synchronizovat <xref:System.Windows.Forms.ToolStripItem.MouseEnter> a <xref:System.Windows.Forms.ToolStripItem.MouseLeave> události.</span><span class="sxs-lookup"><span data-stu-id="cfc4c-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc4c-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfc4c-107">See also</span></span>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [<span data-ttu-id="cfc4c-108">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="cfc4c-108">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
