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
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Postupy: Použití prvku ToolTips v ovládacích prvcích ToolStrip
Můžete zobrazit <xref:System.Windows.Forms.ToolTip> <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> požadovaný ovládací prvek nastavením vlastnosti ovládacího prvku na `true`. <xref:System.Windows.Forms.ToolStrip>  
  
### <a name="to-display-a-tooltip"></a>Zobrazení popisu tlačítka  
  
- Nastavte vlastnost ovládacího prvku na `true`. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
  
     Výchozí hodnota <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je a `true` <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> Výchozíhodnota<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je .`false`  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Použití vlastnosti ToolTipText pro text popisku prvek ToolStripButton  
  
1. Nastavte vlastnost tlačítka na `true`. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
  
2. Nastavte vlastnost tlačítka na `false`. <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>  
  
     `AutoToolTip` Vlastnost je `true` ve výchozím nastavení pro <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>a .<xref:System.Windows.Forms.ToolStripSplitButton>  
  
     Ve výchozím <xref:System.Windows.Forms.ToolTip> nastavení `Text` <xref:System.Windows.Forms.ToolStripButton> používá vlastnost pro text. Pomocí tohoto postupu můžete zobrazit vlastní text v <xref:System.Windows.Forms.ToolStripButton>. <xref:System.Windows.Forms.ToolTip>  
  
> [!NOTE]
> Pokud nastavíte <xref:System.Windows.Forms.ToolStripItemDisplayStyle> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> nebo <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, na tlačítku se nezobrazí žádný text, ale Tip nástroje se stále zobrazuje.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
