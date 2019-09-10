---
title: 'Postupy: Použití aktivačních událostí pro řízení scénáře po spuštění'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855858"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Postupy: Použití aktivačních událostí pro řízení scénáře po spuštění

Tento příklad ukazuje, jak ovládat <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění. Chcete-li <xref:System.Windows.Media.Animation.Storyboard> spustit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pomocí, použijte <xref:System.Windows.Media.Animation.BeginStoryboard>, který distribuuje animace do objektů a vlastností, které animuje, a poté spustí scénář. Pokud pojmenujete <xref:System.Windows.Media.Animation.BeginStoryboard> název zadáním jeho <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> vlastnosti, provedete si ho jako ověřitelné scénář. Pak můžete interaktivní kontrolu scénáře po jeho spuštění.

Použijte následující akce scénáře spolu s <xref:System.Windows.EventTrigger> objekty pro řízení scénáře.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénář.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavený scénář.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změní rychlost scénáře.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Posune scénář na konec období jeho výplně, pokud má nějaký.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénář.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Odstraní scénář, který uvolňuje prostředky.

## <a name="example"></a>Příklad

Následující příklad používá k interaktivnímu řízení scénáře možnosti ovladatelného scénáře.

> [!NOTE]
> Chcete-li zobrazit příklad řízení scénáře pomocí kódu, přečtěte si téma [řízení scénáře po spuštění pomocí interaktivních metod](how-to-control-a-storyboard-after-it-starts.md).

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Další příklady naleznete v [galerii příkladů animace](https://go.microsoft.com/fwlink/?LinkID=159969).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Kontrola scénáře po jeho spuštění pomocí interaktivních metod](how-to-control-a-storyboard-after-it-starts.md)
- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
