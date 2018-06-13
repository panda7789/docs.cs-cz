---
title: 'Postupy: Kumulování hodnot animace při opakujících se cyklech'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 7b954a388549f1bc6f3fa6ec1bcb2df61cc4e045
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557664"
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
 [Přidání výstupní hodnoty animace do počáteční hodnoty animace](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [Opakování animace](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
