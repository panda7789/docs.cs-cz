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
ms.openlocfilehash: 1606db73485944f3dfa8b9c084bffda817520c7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009263"
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TrackBar> ovládací prvek (někdy také nazývané "posuvník") se používá pro procházení velkých množství informací nebo pro úpravu vizuálně číselné nastavení. <xref:System.Windows.Forms.TrackBar> Ovládací prvek má dvě části: thumb, označované také jako ovládací prvek posuvník a osové značky. Jezdce je část, kterou je možné upravit. Jeho pozice koresponduje <xref:System.Windows.Forms.TrackBar.Value%2A> vlastnost. Značky jsou visual indikátory, které jsou rozmístěné v pravidelných intervalech. Pozice přesune v krocích, které zadáte a může být zarovnaný vodorovně nebo svisle. Pruh sledování může například použít k řízení rychlost blikání kurzoru rychlost nebo myši pro systém.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Klíčové vlastnosti <xref:System.Windows.Forms.TrackBar> řízení, představují <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, a <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> je mezery dílků. <xref:System.Windows.Forms.TrackBar.Minimum%2A> a <xref:System.Windows.Forms.TrackBar.Maximum%2A> jsou nejnižší a nejvyšší hodnoty, které lze znázornit na pruh sledování.  
  
 Jsou dva důležité vlastnosti <xref:System.Windows.Forms.TrackBar.SmallChange%2A> a <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. Hodnota <xref:System.Windows.Forms.TrackBar.SmallChange%2A> vlastnost je počet pozic jezdce posune s tím, že stisknuta klávesa vlevo nebo šipka vpravo. Hodnota <xref:System.Windows.Forms.TrackBar.LargeChange%2A> vlastnost je počet pozic jezdce posune s tím, že stisknuté klávese PAGE UP nebo PAGE DOWN nebo v reakci na myši klikne na pruh sledování na obou stranách jezdce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TrackBar>
- [Ovládací prvek TrackBar](trackbar-control-windows-forms.md)
