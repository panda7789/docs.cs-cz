---
title: "Postupy: Použití prvku ToolTips v ovládacích prvcích ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d81a1936d8a6159c6225a12f712c546fe9beeb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Postupy: Použití prvku ToolTips v ovládacích prvcích ToolStrip
Můžete zobrazit <xref:System.Windows.Forms.ToolTip> pro <xref:System.Windows.Forms.ToolStrip> ovládacího prvku, chcete-li nastavením ovládacího prvku <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> vlastnost `true`.  
  
### <a name="to-display-a-tooltip"></a>Zobrazení popisu tlačítka  
  
-   Nastavte <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> vlastnost ovládacího prvku na `true`.  
  
     Výchozí hodnota <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je `true`a výchozí hodnota <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> je `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Chcete použít pro text popisu tlačítka ovládací prvek ToolStripButton ToolTipText – vlastnost  
  
1.  Nastavte <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> vlastnost tlačítko pro `true`.  
  
2.  Nastavte <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> vlastnost tlačítko pro `false`.  
  
     `AutoToolTip` Vlastnost je `true` ve výchozím nastavení pro <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, a <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     A <xref:System.Windows.Forms.ToolStripButton> používá jeho `Text` vlastnost <xref:System.Windows.Forms.ToolTip> text ve výchozím nastavení. Pomocí tohoto postupu můžete zobrazit ve vlastní text <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Pokud nastavíte <xref:System.Windows.Forms.ToolStripItemDisplayStyle> k <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> nebo <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, žádný text se zobrazí na tlačítko, ale stále nezobrazí popis.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
