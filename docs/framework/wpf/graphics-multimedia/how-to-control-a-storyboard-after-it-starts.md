---
title: 'Postupy: Řízení scénáře po jeho spuštění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855860"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Postupy: Řízení scénáře po jeho spuštění

Tento příklad ukazuje, jak použít kód k řízení a <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění. Pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]řízení scénáře v, použití <xref:System.Windows.Trigger> a <xref:System.Windows.TriggerAction> objektů; příklad naleznete v tématu [použití triggerů událostí k řízení scénáře po jeho spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

Chcete-li spustit scénář, použijte jeho <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu, která distribuuje animace scénáře do vlastností, které animuje, a spustí scénář.

Chcete-li nastavit scénář jako ovladatelné, použijte <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu a jako druhý parametr zadejte **hodnotu true** . Pak můžete pomocí interaktivních metod scénáře pozastavit, obnovit, vyhledat, zastavit, zrychlit nebo zpomalit scénář nebo ho posunout na jeho dobu vyplňování. Následuje seznam interaktivních metod scénáře:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pozastaví scénář.

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Obnoví pozastavený scénář.

- <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Nastaví interaktivní rychlost scénáře.

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Vyhledá scénář v zadaném umístění.

- <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Vyhledá scénář do určeného umístění. Na rozdíl od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody je tato operace zpracována před další značkou.

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Posune scénář do jeho tečky Fill, pokud má nějaký.

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Zastaví scénář.

V následujícím příkladu se k interaktivnímu řízení scénáře používají několik metod scénáře.

> [!NOTE]
> Příklad řízení scénáře pomocí aktivačních událostí s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]najdete v tématu [použití triggerů událostí k řízení scénáře po jeho spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

## <a name="example"></a>Příklad

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a>Viz také:

- [Použití aktivačních událostí pro řízení scénáře po spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
