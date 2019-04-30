---
title: Přehled ovládacích prvků HScrollBar a VScrollBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
ms.openlocfilehash: d4a7912a5781fc583357affa728f7d81059b5cf9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928569"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>Přehled ovládacích prvků HScrollBar a VScrollBar (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ScrollBar> ovládací prvky se používají k zajištění snadnou navigaci prostřednictvím dlouhý seznam položek nebo velké množství informací posunutím buď vodorovně nebo svisle v rámci aplikace nebo ovládacího prvku. Posuvníky jsou běžné prvek rozhraní Windows proto <xref:System.Windows.Forms.ScrollBar> ovládací prvek se často používá s ovládacími prvky, které nejsou odvozeny od <xref:System.Windows.Forms.ScrollableControl> třídy. Podobně, zvolte mnoho vývojářů začlenit <xref:System.Windows.Forms.ScrollBar> řízení při vytváření vlastních uživatelských ovládacích prvků.  
  
 <xref:System.Windows.Forms.HScrollBar> (Vodorovně) a <xref:System.Windows.Forms.VScrollBar> ovládacích prvků (svislé) fungovat nezávisle z jiných ovládacích prvků a mají své vlastní sadu událostí, vlastnosti a metody. <xref:System.Windows.Forms.ScrollBar> ovládací prvky nejsou stejná jako integrované posuvníků, které jsou připojeny k textová pole, pole se seznamem, pole se seznamem nebo formuláře MDI ( <xref:System.Windows.Forms.TextBox> má ovládací prvek <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnosti chcete zobrazit nebo skrýt posuvníky, které jsou připojené do ovládacího prvku).  
  
 <xref:System.Windows.Forms.ScrollBar> Řídí použití <xref:System.Windows.Forms.ScrollBar.Scroll> události ke sledování pohybu posuvníku (někdy označované jako jezdce) podél posuvníku. Použití <xref:System.Windows.Forms.ScrollBar.Scroll> události poskytuje přístup k hodnotě panelu přejděte ho přetáhnout.  
  
## <a name="value-property"></a>Value – vlastnost  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> Vlastnost (která je ve výchozím nastavení, 0) je `integer` hodnotu odpovídající pozice posuvníku v posuvníku. Když pozice posuvníku v minimální hodnota, přesune se do nejvíce vlevo umístění (vodorovné posuvníky) nebo nahoře (pro svislé posuvníky). Pokud posouvacího políčka je maximální hodnota, přejde box přejděte úplně vpravo nebo dolní pozici. Obdobně hodnotu uprostřed mezi dolní a horní části rozsahu umístí hrany posouvacího políčka uprostřed posuvníku.  
  
 Kromě použití kliknutí myší, chcete-li změnit hodnotu posuvníku panelu, můžete uživatele také přetáhnout posouvacího políčka do libovolného bodu podél pruhu. Výsledná hodnota závisí na pozice posuvníku, ale je vždycky v rozsahu <xref:System.Windows.Forms.ScrollBar.Minimum%2A> k <xref:System.Windows.Forms.ScrollBar.Maximum%2A> vlastnosti nastavené uživatelem.  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange a SmallChange vlastnosti  
 Když uživatel stiskne klávesu PAGE UP nebo PAGE DOWN nebo klikne na tlačítko v panelu sledování přejděte na obou stranách posuvníku, <xref:System.Windows.Forms.ScrollBar.Value%2A> změny vlastností podle hodnoty nastavené <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> vlastnost.  
  
 Když uživatel stiskne jeden šipky klíče nebo kliknutí na jedno z tlačítek posuvníku panelu, <xref:System.Windows.Forms.ScrollBar.Value%2A> změny vlastností podle hodnoty nastavené <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
