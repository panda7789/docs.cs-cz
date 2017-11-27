---
title: "Přehled ovládacích prvků HScrollBar a VScrollBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80ec592bf83969ae57495b0df2af110b5622ea11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>Přehled ovládacích prvků HScrollBar a VScrollBar (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ScrollBar> používají se ovládací prvky pro navigaci v seznamu položek nebo velké množství informací posouváním buď vodorovně nebo svisle v rámci aplikace nebo ovládací prvek. Posuvníky jsou běžné element rozhraní systému Windows, proto <xref:System.Windows.Forms.ScrollBar> ovládací prvek se často používá s ovládacími prvky, které není odvozena od <xref:System.Windows.Forms.ScrollableControl> třídy. Podobně se celá řada vývojářů rozhodnete začlenit <xref:System.Windows.Forms.ScrollBar> řízení při vytváření vlastní uživatelské ovládací prvky.  
  
 <xref:System.Windows.Forms.HScrollBar> (Vodorovně) a <xref:System.Windows.Forms.VScrollBar> (svislé) ovládacích prvků fungovat nezávisle z jiných ovládacích prvků a mít vlastní sadu událostí, vlastnosti a metody. <xref:System.Windows.Forms.ScrollBar>ovládací prvky nejsou stejná jako integrované posuvníky, které jsou připojené k textová pole, seznamy, pole se seznamem nebo formulářů MDI ( <xref:System.Windows.Forms.TextBox> má ovládací prvek <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnosti chcete zobrazit nebo skrýt posuvníky, které jsou připojené k ovládacímu prvku).  
  
 <xref:System.Windows.Forms.ScrollBar> Řídí použití <xref:System.Windows.Forms.ScrollBar.Scroll> události k monitorování přesun od jezdce (někdy označované jako úchytu) podél posuvníku. Pomocí <xref:System.Windows.Forms.ScrollBar.Scroll> událostí poskytuje přístup k hodnotě panelu přejděte, jako je právě přetáhli.  
  
## <a name="value-property"></a>Value – vlastnost  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> Vlastnost (která je ve výchozím nastavení, 0) je `integer` hodnotu odpovídající pozice jezdce posuvníku. Když na pozici posunutí pole na minimální hodnotu, přesune na pozici nejvíce vlevo (pro vodorovné posuvníky) nebo nejvyšší pozici (pro svislé posuvníky). Když posouvací políčko je na maximální hodnotu, posuňte pole přesun do nejvíce vpravo nebo dolní pozici. Podobně hodnotu uprostřed mezi dolní a horní části rozsahu, umístí úvodní hrany posouvacího políčka uprostřed posuvníku.  
  
 Kromě použití ke změně hodnoty panelu přejděte myší, můžete uživatele také přetáhnout posouvací políčko do jakéhokoli bodu na panelu. Výsledná hodnota závisí na pozici posouvací políčko, ale je vždy v rozsahu <xref:System.Windows.Forms.ScrollBar.Minimum%2A> k <xref:System.Windows.Forms.ScrollBar.Maximum%2A> vlastnosti nastavený uživatelem.  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange a SmallChange vlastnosti  
 Když uživatel stiskne klávesu PAGE UP nebo PAGE DOWN nebo klikne v sledovat panelu přejděte na obou stranách posouvací políčko, <xref:System.Windows.Forms.ScrollBar.Value%2A> změny vlastností podle hodnotu nastavenou v <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> vlastnost.  
  
 Když uživatel stiskne jednu šipku klíče nebo klepne na jednu z tlačítka panelu přejděte <xref:System.Windows.Forms.ScrollBar.Value%2A> změny vlastností podle hodnotu nastavenou v <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [Přidání do Windows Forms pro rozhraní .NET Framework 2.0](http://msdn.microsoft.com/en-us/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [Ovládací prvky používané ve formulářích Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
