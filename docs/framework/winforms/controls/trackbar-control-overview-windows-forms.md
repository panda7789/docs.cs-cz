---
title: TrackBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: d0a0cbbcc618e2fa52b3719bcc8f0135a1e0752e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TrackBar> ovládací prvek (také někdy nazývané "posuvník") se používá pro procházení velké množství informací nebo vizuálně úpravě číselné nastavení. <xref:System.Windows.Forms.TrackBar> Řízení má dvě části: jezdce, také známé jako jezdce a značek. Jezdce je část, která se dá upravit. Odpovídá jeho umístění <xref:System.Windows.Forms.TrackBar.Value%2A> vlastnost. Značky jsou visual indikátory, které jsou rozmístěny v pravidelných intervalech. Pozice přesouvají v krocích, které můžete zadat a lze zarovnávat vodorovně nebo svisle. Panelu sledování můžete například použít k řízení rychlost blikání kurzoru míry nebo myš pro systém.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti <xref:System.Windows.Forms.TrackBar> řízení, představují <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, a <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> je mezery o rysky. <xref:System.Windows.Forms.TrackBar.Minimum%2A> a <xref:System.Windows.Forms.TrackBar.Maximum%2A> jsou nejnižší a nejvyšší hodnoty, které může být reprezentován na panelu sledovat.  
  
 Jsou dvě důležité vlastnosti <xref:System.Windows.Forms.TrackBar.SmallChange%2A> a <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. Hodnota <xref:System.Windows.Forms.TrackBar.SmallChange%2A> vlastnost je počet pozic úchytu přesune v reakci na LEVÉ a pravé šipky klíče stisknutí tlačítka. Hodnota <xref:System.Windows.Forms.TrackBar.LargeChange%2A> vlastnost je počet pozic úchytu přesune v reakci na situaci, kdy stisknuta klávesa PAGE UP nebo PAGE DOWN nebo v reakci na myši klikne na panelu sledovat na obou stranách od jezdce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TrackBar>  
 [Ovládací prvek TrackBar](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
