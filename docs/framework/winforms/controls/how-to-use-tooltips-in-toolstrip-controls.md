---
title: 'Postupy: Použití prvku ToolTips v ovládacích prvcích ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: b009d19ed949edbd52ec02252ba1e2271e4cb738
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750555"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Postupy: Použití prvku ToolTips v ovládacích prvcích ToolStrip
Můžete zobrazit <xref:System.Windows.Forms.ToolTip> pro <xref:System.Windows.Forms.ToolStrip> ovládacího prvku chcete nastavením ovládacího prvku <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> vlastnost `true`.  
  
### <a name="to-display-a-tooltip"></a>Chcete-li zobrazit popis  
  
- Nastavte <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> vlastnost ovládacího prvku na `true`.  
  
     Výchozí hodnota <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je `true`a výchozí hodnota <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Pro účely text popisku ovládací prvek ToolStripButton ToolTipText – vlastnost  
  
1. Nastavte <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> vlastnosti tlačítka `true`.  
  
2. Nastavte <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> vlastnosti tlačítka `false`.  
  
     `AutoToolTip` Vlastnost `true` ve výchozím nastavení pro <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, a <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     A <xref:System.Windows.Forms.ToolStripButton> používá jeho `Text` vlastnost <xref:System.Windows.Forms.ToolTip> text ve výchozím nastavení. Tento postup slouží k zobrazení vlastního textu v <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Pokud nastavíte <xref:System.Windows.Forms.ToolStripItemDisplayStyle> k <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> nebo <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, se nezobrazí žádný text na tlačítku, ale stále se zobrazí popis tlačítka.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
