---
title: 'Postupy: Použití prvku ToolTips v ovládacích prvcích ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 2b10b3fcf3930d5848f1d7a9602cfcc945bc8975
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534070"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="d1f16-102">Postupy: Použití prvku ToolTips v ovládacích prvcích ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d1f16-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="d1f16-103">Můžete zobrazit <xref:System.Windows.Forms.ToolTip> pro <xref:System.Windows.Forms.ToolStrip> ovládacího prvku, chcete-li nastavením ovládacího prvku <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="d1f16-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="d1f16-104">Zobrazení popisu tlačítka</span><span class="sxs-lookup"><span data-stu-id="d1f16-104">To display a ToolTip</span></span>  
  
-   <span data-ttu-id="d1f16-105">Nastavte <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> vlastnost ovládacího prvku na `true`.</span><span class="sxs-lookup"><span data-stu-id="d1f16-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="d1f16-106">Výchozí hodnota <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je `true`a výchozí hodnota <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je `false`.</span><span class="sxs-lookup"><span data-stu-id="d1f16-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="d1f16-107">Chcete použít pro text popisu tlačítka ovládací prvek ToolStripButton ToolTipText – vlastnost</span><span class="sxs-lookup"><span data-stu-id="d1f16-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1.  <span data-ttu-id="d1f16-108">Nastavte <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> vlastnost tlačítko pro `true`.</span><span class="sxs-lookup"><span data-stu-id="d1f16-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2.  <span data-ttu-id="d1f16-109">Nastavte <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> vlastnost tlačítko pro `false`.</span><span class="sxs-lookup"><span data-stu-id="d1f16-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="d1f16-110">`AutoToolTip` Vlastnost je `true` ve výchozím nastavení pro <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, a <xref:System.Windows.Forms.ToolStripSplitButton>.</span><span class="sxs-lookup"><span data-stu-id="d1f16-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="d1f16-111">A <xref:System.Windows.Forms.ToolStripButton> používá jeho `Text` vlastnost <xref:System.Windows.Forms.ToolTip> text ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d1f16-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="d1f16-112">Pomocí tohoto postupu můžete zobrazit ve vlastní text <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="d1f16-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1f16-113">Pokud nastavíte <xref:System.Windows.Forms.ToolStripItemDisplayStyle> k <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> nebo <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, žádný text se zobrazí na tlačítko, ale stále nezobrazí popis.</span><span class="sxs-lookup"><span data-stu-id="d1f16-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f16-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1f16-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [<span data-ttu-id="d1f16-115">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d1f16-115">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
