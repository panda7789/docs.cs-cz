---
title: 'Postupy: Kontrola scénáře po jeho spuštění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 107391386dfbb718f9436d9a039b08439fbc3279
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762134"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Postupy: Kontrola scénáře po jeho spuštění
Tento příklad ukazuje způsob použití kódu pro ovládací prvek <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění. Pro řízení scénáře v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte <xref:System.Windows.Trigger> a <xref:System.Windows.TriggerAction> objekty; příklad najdete v tématu [pomocí aktivačních procedur událostí pro řízení scénáře po jeho spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
 Spusťte scénáře pomocí jeho <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu, která distribuuje do scénáře animace vlastností animace a spuštění scénáře.  
  
 Aby scénáře může ovládat, můžete použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu a zadejte **true** jako druhý parametr. Potom můžete interaktivních metod do scénáře pozastavení, obnovení, hledání, zastavit, urychlit, nebo zpomalit scénáři nebo přejděte na svůj. Následuje seznam interaktivních metod do scénáře:  
  
- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pozastaví scénáři.  
  
- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Obnoví pozastavenou scénáře.  
  
- <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Nastaví interaktivní rychlost do scénáře.  
  
- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Vyhledá scénáře zadaného umístění.  
  
- <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Vyhledá scénáře do zadaného umístění. Na rozdíl od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodu, tato operace se zpracovává před další značky.  
  
- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Scénář tak, aby jeho období výplně záloh, má-li nějaký.  
  
- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Zastaví scénáři.  
  
 V následujícím příkladu slouží několik metod scénáře pro interaktivní řízení scénáře.  
  
 **Poznámka:** Chcete-li zobrazit příklad řízení scénáře pomocí aktivačních procedur s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], naleznete v tématu [použitím aktivačních procedur událostí pro řízení scénáře po jeho spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Použití aktivačních událostí pro řízení scénáře po spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
