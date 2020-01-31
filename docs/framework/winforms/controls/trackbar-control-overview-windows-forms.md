---
title: TrackBar – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 6901405100df4633c84850757f55b756bc9a0199
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741468"
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.TrackBar> (někdy označovaný také jako "ovládací prvek" posuvníku) se používá k procházení velkého množství informací nebo k vizuální úpravě číselného nastavení. Ovládací prvek <xref:System.Windows.Forms.TrackBar> má dvě části: palec, označované také jako posuvník, a značky. Palec je součást, kterou lze upravit. Jeho poloha odpovídá vlastnosti <xref:System.Windows.Forms.TrackBar.Value%2A>. Značky jsou vizuální indikátory, které jsou rozmístěny v pravidelných intervalech. TrackBar se přesune v přírůstcích, které zadáte, a dá se Zarovnat vodorovně nebo svisle. Například můžete použít panel sledování k řízení rychlosti blikání kurzoru nebo rychlosti myši pro systém.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti ovládacího prvku <xref:System.Windows.Forms.TrackBar> jsou <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>a <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> je mezery mezi značkami. <xref:System.Windows.Forms.TrackBar.Minimum%2A> a <xref:System.Windows.Forms.TrackBar.Maximum%2A> jsou nejmenší a největší hodnoty, které lze znázornit na panelu sledování.  
  
 Existují dvě další důležité vlastnosti <xref:System.Windows.Forms.TrackBar.SmallChange%2A> a <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. Hodnota vlastnosti <xref:System.Windows.Forms.TrackBar.SmallChange%2A> je počet pozic, po které se posune pohyb v reakci na stisknutí klávesy šipka vlevo nebo vpravo. Hodnota vlastnosti <xref:System.Windows.Forms.TrackBar.LargeChange%2A> je počet pozic, o které se posune Miniatura v reakci na stisknutí klávesy PAGE UP nebo PAGE DOWN, nebo v reakci na tlačítko myši na panelu sledování na kterékoli straně jezdce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TrackBar>
- [Ovládací prvek TrackBar](trackbar-control-windows-forms.md)
