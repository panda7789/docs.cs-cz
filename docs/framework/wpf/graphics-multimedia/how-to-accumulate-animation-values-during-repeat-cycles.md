---
title: "Postupy: Kumulování hodnot animace při opakujících se cyklech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4abe19f4548ed41eb19ae4dffb37b832a7df71d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a>Postupy: Kumulování hodnot animace při opakujících se cyklech
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost hromadit hodnoty animace napříč opakovaných cyklů.  
  
## <a name="example"></a>Příklad  
 Použití <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost hromadit základní hodnoty animace napříč opakovaných cyklů. Například pokud nastavíte animace opakování 9 časy (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") a nastavte vlastnosti, která má animace 10 až 15 (z = 10 k = 15), vlastnost animuje od 10 do 15 první cyklu od 15 do 20 druhý cyklu , z 20 až 25 během třetí cyklu a tak dále. Proto každý cyklus animace používá koncovou hodnotu animace z předchozího cyklu animace jako svou základní hodnotu.  
  
 Můžete použít `IsCumulative` vlastnost nejzákladnější animace a většina klíčových snímků animace. Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Následující příklad ukazuje toto chování animace šířku čtyři obdélníky. Příklad:  
  
-   Animuje první rámeček s <xref:System.Windows.Media.Animation.DoubleAnimation> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost `true`.  
  
-   Animuje druhý rámeček s <xref:System.Windows.Media.Animation.DoubleAnimation> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost, která má výchozí hodnotu `false`.  
  
-   Animuje třetí rámeček s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> vlastnost `true`.  
  
-   Animuje poslední rámeček s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> vlastnost `false`.  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Přidejte hodnotu animace výstup do animace počáteční hodnota](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [Opakování animace](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled animací jednotlivých klíč](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
