---
title: 'Postupy: Použití prvku ToolTips v ovládacích prvcích ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939735"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="814af-102">Postupy: Použití prvku ToolTips v ovládacích prvcích ToolStrip</span><span class="sxs-lookup"><span data-stu-id="814af-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="814af-103">Můžete zobrazit <xref:System.Windows.Forms.ToolTip> <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> požadovaný ovládací prvek nastavením vlastnosti ovládacího prvku na `true`. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="814af-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="814af-104">Zobrazení popisu tlačítka</span><span class="sxs-lookup"><span data-stu-id="814af-104">To display a ToolTip</span></span>  
  
- <span data-ttu-id="814af-105">Nastavte vlastnost ovládacího prvku na `true`. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A></span><span class="sxs-lookup"><span data-stu-id="814af-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="814af-106">Výchozí hodnota <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je a `true` <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> Výchozíhodnota<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je .`false`</span><span class="sxs-lookup"><span data-stu-id="814af-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="814af-107">Použití vlastnosti ToolTipText pro text popisku prvek ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="814af-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1. <span data-ttu-id="814af-108">Nastavte vlastnost tlačítka na `true`. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A></span><span class="sxs-lookup"><span data-stu-id="814af-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2. <span data-ttu-id="814af-109">Nastavte vlastnost tlačítka na `false`. <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="814af-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="814af-110">`AutoToolTip` Vlastnost je `true` ve výchozím nastavení pro <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>a .<xref:System.Windows.Forms.ToolStripSplitButton></span><span class="sxs-lookup"><span data-stu-id="814af-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="814af-111">Ve výchozím <xref:System.Windows.Forms.ToolTip> nastavení `Text` <xref:System.Windows.Forms.ToolStripButton> používá vlastnost pro text.</span><span class="sxs-lookup"><span data-stu-id="814af-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="814af-112">Pomocí tohoto postupu můžete zobrazit vlastní text v <xref:System.Windows.Forms.ToolStripButton>. <xref:System.Windows.Forms.ToolTip></span><span class="sxs-lookup"><span data-stu-id="814af-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="814af-113">Pokud nastavíte <xref:System.Windows.Forms.ToolStripItemDisplayStyle> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> nebo <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, na tlačítku se nezobrazí žádný text, ale Tip nástroje se stále zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="814af-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814af-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="814af-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="814af-115">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="814af-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
