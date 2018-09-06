---
title: 'Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: f31b1233f00147fdccde5e0816fa4839ae33d549
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036389"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění
Tento příklad ukazuje, jak řídit <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění. Spustit <xref:System.Windows.Media.Animation.Storyboard> pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte <xref:System.Windows.Media.Animation.BeginStoryboard>, který distribuuje animace objektů a vlastností animace a pak spustí scénáři. Pokud dáte <xref:System.Windows.Media.Animation.BeginStoryboard> název tak, že zadáte jeho <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> vlastnost, provedete to může ovládat scénáře. Pak můžete interaktivně ovládat scénáře po jeho spuštění.  
  
 Použijte následující scénáře akce spolu s <xref:System.Windows.EventTrigger> objekty pro řízení scénáře.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénáři.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavenou scénáře.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změní rychlost scénáře.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Pokročilé funkce scénáře do konce období výplň, má-li nějaký.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénáři.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Odstraní scénáři uvolnit prostředky.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá akce může ovládat scénáře pro interaktivní řízení scénáře.  
  
 **Poznámka:** příklad scénáře řízení pomocí kódu najdete v tématu [řízení scénáře po jeho spuštění pomocí její interaktivní metody](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Další příklady najdete v článku [animace příkladu Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [Kontrola scénáře po jeho spuštění pomocí interaktivních metod](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
