---
title: 'Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186705"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění

Tento příklad ukazuje, <xref:System.Windows.Media.Animation.Storyboard> jak řídit po spuštění. Chcete-li <xref:System.Windows.Media.Animation.Storyboard> spustit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pomocí <xref:System.Windows.Media.Animation.BeginStoryboard>, použijte , který distribuuje animace na objekty a vlastnosti, které animovat a pak spustí scénář. Pokud zadáte <xref:System.Windows.Media.Animation.BeginStoryboard> název zadáním <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> jeho vlastnosti, uděláte z něj kontrolovatelný scénář. Potom můžete interaktivně řídit scénář po jeho spuštění.

Použijte následující akce scénáře <xref:System.Windows.EventTrigger> spolu s objekty k ovládání scénáře.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénář.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavený scénář.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změní rychlost scénáře.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Posune scénář na konec jeho výplně období, pokud má jeden.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénář.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Odebere scénář a uvolní prostředky.

## <a name="example"></a>Příklad

Následující příklad používá kontrolovatelné akce scénáře k interaktivnímu řízení scénáře.

> [!NOTE]
> Chcete-li zobrazit příklad řízení scénáře pomocí kódu, najdete v [tématu Ovládání scénáře po spuštění pomocí jeho interaktivní metody](how-to-control-a-storyboard-after-it-starts.md).

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Další příklady naleznete v [galerii příkladů animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Kontrola scénáře po jeho spuštění pomocí interaktivních metod](how-to-control-a-storyboard-after-it-starts.md)
- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
