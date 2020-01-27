---
title: Přehled ovládacích prvků HScrollBar a VScrollBar
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
ms.openlocfilehash: abe0c8da9723f17cb80715454f6ab7297724a21f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728170"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>Přehled ovládacích prvků HScrollBar a VScrollBar (Windows Forms)
Model Windows Forms <xref:System.Windows.Forms.ScrollBar> ovládací prvky slouží k zajištění snadné navigace prostřednictvím dlouhého seznamu položek nebo velkého množství informací posouváním vodorovně nebo svisle v rámci aplikace nebo ovládacího prvku. Posuvníky jsou běžným prvkem rozhraní systému Windows, takže <xref:System.Windows.Forms.ScrollBar> ovládací prvek se často používá s ovládacími prvky, které nejsou odvozeny od <xref:System.Windows.Forms.ScrollableControl> třídy. Podobně mnoho vývojářů při vytváření vlastních uživatelských ovládacích prvků zvolí ovládací prvek <xref:System.Windows.Forms.ScrollBar>.  
  
 Ovládací prvky <xref:System.Windows.Forms.HScrollBar> (vodorovné) a <xref:System.Windows.Forms.VScrollBar> (vertikálně) pracují nezávisle na jiných ovládacích prvcích a mají vlastní sadu událostí, vlastností a metod. ovládací prvky <xref:System.Windows.Forms.ScrollBar> se neshodují s vestavěnými posuvníky, které jsou připojeny k textovým polím, seznamům, polím se seznamem nebo formuláři MDI (ovládací prvek <xref:System.Windows.Forms.TextBox> má vlastnost <xref:System.Windows.Forms.TextBox.ScrollBars%2A> k zobrazení nebo skrytí posuvníků, které jsou připojeny k ovládacímu prvku).  
  
 Ovládací prvky <xref:System.Windows.Forms.ScrollBar> používají událost <xref:System.Windows.Forms.ScrollBar.Scroll> k monitorování přesunu posuvníku (někdy označovaného jako palec) podél posuvníku. Použití události <xref:System.Windows.Forms.ScrollBar.Scroll> poskytuje přístup k hodnotě posuvníku při jejím přetahování.  
  
## <a name="value-property"></a>Value – vlastnost  
 Vlastnost <xref:System.Windows.Forms.ScrollBar.Value%2A> (ve výchozím nastavení je 0) je `integer` hodnota odpovídající pozici posuvníku na posuvníku. Když je pozice posuvníku minimální hodnotou, přesune se na pozici vlevo (pro vodorovné posuvníky) nebo na horní pozici (pro svislé posuvníky). Pokud je rolovací pole v maximální hodnotě, přesune se posuvník do nejvyšší nebo nejnižší pozice. Podobně hodnota uprostřed mezi dolním a horním okrajem umístí přední okraj posuvníku uprostřed posuvníku.  
  
 Kromě použití kliknutí myší ke změně hodnoty posuvníku může uživatel také přetáhnout posuvník do libovolného bodu podél pruhu. Výsledná hodnota závisí na pozici posuvníku, ale je vždy v rámci rozsahu <xref:System.Windows.Forms.ScrollBar.Minimum%2A> <xref:System.Windows.Forms.ScrollBar.Maximum%2A> vlastností nastavených uživatelem.  
  
## <a name="largechange-and-smallchange-properties"></a>Vlastnosti LargeChange a SmallChange  
 Když uživatel stiskne klávesu PAGE UP nebo PAGE DOWN nebo klikne na posuvníky na kterékoli straně posuvníku, změní se vlastnost <xref:System.Windows.Forms.ScrollBar.Value%2A> podle hodnoty nastavené ve vlastnosti <xref:System.Windows.Forms.ScrollBar.LargeChange%2A>.  
  
 Když uživatel stiskne jednu z kláves se šipkami nebo klikne na jedno z tlačítek posuvníku, vlastnost <xref:System.Windows.Forms.ScrollBar.Value%2A> se změní podle hodnoty nastavené ve vlastnosti <xref:System.Windows.Forms.ScrollBar.SmallChange%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
