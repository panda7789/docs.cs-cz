---
title: "Postupy: Kontrola scénáře po jeho spuštění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b28cdf3b653925a5856c0bc9def5aebb9fdc6c14
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Postupy: Kontrola scénáře po jeho spuštění
Tento příklad ukazuje, jak použít kód na ovládací prvek <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění. K řízení storyboard v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte <xref:System.Windows.Trigger> a <xref:System.Windows.TriggerAction> objekty; příklad, naleznete v části [aktivační události použít k řízení scénáře po jeho spuštění](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
 Spusťte scénáře pomocí jeho <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu, která distribuuje animace do scénáře pro vlastnosti se animace a spustí scénáři.  
  
 Chcete-li řídit scénáře, můžete použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda a zadejte **true** jako druhý parametr. Potom můžete do scénáře interaktivního metody pozastavit, obnovit, hledání, zastavit, zrychlit, nebo zpomalit scénáři nebo přechodu na jeho výplně období. Následuje seznam do scénáře interaktivního metod:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pozastaví scénáři.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Obnoví pozastavenou scénáře.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Nastaví do scénáře interaktivního rychlost.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Cílem je storyboard v zadaném umístění.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Cílem je storyboard do zadaného umístění. Na rozdíl od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metoda, tato operace se zpracují dříve, než další značky.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Přejde storyboard jeho výplně dobu, pokud jej obsahuje.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Zastaví scénáři.  
  
 V následujícím příkladu slouží několik metod storyboard interaktivně řídit scénáře.  
  
 **Poznámka:** příklad řízení storyboard, pomocí aktivačních událostí, jejichž [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najdete v části [aktivační události použít k řízení scénáře po jeho spuštění](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Použít k řízení scénáře po jeho spuštění aktivačních událostí](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
