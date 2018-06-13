---
title: 'Postupy: Nastavení trvání pro animaci'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: df9e12e1bd3a365c3013d0f75df663bd46186ee2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561372"
---
# <a name="how-to-set-a-duration-for-an-animation"></a>Postupy: Nastavení trvání pro animaci
A <xref:System.Windows.Media.Animation.Timeline> představuje segment čas a že segmentu je dáno časové ose <xref:System.Windows.Duration>. Když <xref:System.Windows.Media.Animation.Timeline> dosáhne konce z jeho trvání, zastaví se přehrávání. Pokud <xref:System.Windows.Media.Animation.Timeline> má podřízené časových os, přestane také přehrávání. V případě animace <xref:System.Windows.Duration> Určuje, jak dlouho animace trvá přechod z jeho výchozí hodnotu na jeho koncovou hodnotu.  
  
 Můžete zadat <xref:System.Windows.Duration> s konkrétní, konečný čas nebo speciální hodnoty <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>. Doba trvání animace na musí být vždy hodnotu času, protože animace musí mít vždy definované, konečné délku –, jinak nebude animace vědět, jak přecházet mezi jeho cílové hodnoty. Kontejner časové osy (<xref:System.Windows.Media.Animation.TimelineGroup> objekty), jako například <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.ParallelTimeline>, výchozí doba trvání <xref:System.Windows.Duration.Automatic%2A>, což znamená, že automaticky ukončí při jejich posledního podřízeného zastavení přehrávání.  
  
 V následujícím příkladu, šířky, výšky a výplně barva <xref:System.Windows.Shapes.Rectangle> je animace. Doby jsou nastavené na animace a kontejner časové osy které animace účinky, včetně řízení dosahovaný rychlost animace a přepsáním trvání časové osy podřízeného s trvání časová osa kontejneru.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Duration>  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
