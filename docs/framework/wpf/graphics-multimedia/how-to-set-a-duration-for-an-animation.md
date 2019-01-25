---
title: 'Postupy: Nastavení trvání pro animaci'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: 7a2edbd953f648d5555e5dc50469211a6da066de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497928"
---
# <a name="how-to-set-a-duration-for-an-animation"></a>Postupy: Nastavení trvání pro animaci
A <xref:System.Windows.Media.Animation.Timeline> představuje segment čas a délka tohoto segmentu se zakládá na časové ose <xref:System.Windows.Duration>. Když <xref:System.Windows.Media.Animation.Timeline> dosažení konce jeho trvání, zastaví přehrávání. Pokud <xref:System.Windows.Media.Animation.Timeline> má podřízených časových os, vyhodnocování se zastaví přehrávání také. V případě animace <xref:System.Windows.Duration> Určuje, jak dlouho animace trvá přechod z jeho výchozí hodnotu na jeho koncovou hodnotu.  
  
 Můžete zadat <xref:System.Windows.Duration> s konkrétní, omezené dobu nebo speciálními hodnotami <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>. Doba trvání pro animaci musí být vždy časové hodnoty, protože animace vždy musí mít délku definovanou, omezené – jinak nebude animace vědět, jak přecházet mezi jeho cílové hodnoty. Časové osy kontejneru (<xref:System.Windows.Media.Animation.TimelineGroup> objekty), jako například <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.ParallelTimeline>, výchozí doba trvání <xref:System.Windows.Duration.Automatic%2A>, což znamená, že automaticky ukončí po jejich posledního podřízeného zastaví přehrávání.  
  
 V následujícím příkladu, šířku, výšku a výplň barvu <xref:System.Windows.Shapes.Rectangle> je animovaný. Doba trvání jsou nastavené na časové ose animace a kontejner výsledkem efekty animace včetně řízení zjištěné rychlosti animace a přepsáním trvání podřízených časových os s dobou trvání časové osy kontejneru.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Duration>
- [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
