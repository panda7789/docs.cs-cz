---
title: "Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9e096969713cc4b9c42261b238691d51cb49d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění
Tento příklad ukazuje, jak řídit <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění. Spuštění <xref:System.Windows.Media.Animation.Storyboard> pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte <xref:System.Windows.Media.Animation.BeginStoryboard>, který distribuuje animace objektů a vlastností se animace a pak spustí scénáři. Pokud zadáte název <xref:System.Windows.Media.Animation.BeginStoryboard> název zadáním jeho <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> vlastnost, provedete ho ovladatelné scénáře. Pak můžete interaktivně ovládat scénáři po jeho spuštění.  
  
 Použít následující akce storyboard společně s <xref:System.Windows.EventTrigger> objekty k řízení scénáře.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénáři.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavenou scénáře.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změny rychlosti scénáře.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Pokud má jedna přejde storyboard na konci období jeho výplně.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénáři.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Odebere storyboard, tím uvolní prostředky.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá ovladatelné storyboard akce interaktivně řídit scénáře.  
  
 **Poznámka:** příklad řízení scénáře pomocí kódu najdete v sekci [řídit scénáře po jeho spuštění pomocí její interaktivní metody](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Další příklady najdete v tématu [animace příklad Galerie](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [Po zahájení používání její interaktivní metody řízení scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
