---
title: 'Postupy: Kumulování hodnot animace při opakujících se cyklech'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 4b739883322751e2df86e13bfd07249abdb10a08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762173"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a>Postupy: Kumulování hodnot animace při opakujících se cyklech
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost kumulování hodnot animace přes opakující se cykly.  
  
## <a name="example"></a>Příklad  
 Použití <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost kumulování základních hodnot animace přes opakující se cykly. Například pokud nastavíte animace opakování 9 časy (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") a nastavte vlastnost animovat 10 až 15 (z = 10 k = 15), vlastnost animuje z 10 až 15 během první cyklu z 15 až 20 během druhé cyklu , od 20 do 25 během cyklu třetí a tak dále. Každý cyklus animace proto používá koncovou hodnotu animace od předchozího cyklu animace jako jeho základní hodnoty.  
  
 Můžete použít `IsCumulative` vlastnost nejzákladnější animace a většina klíčový snímek animace. Další informace najdete v tématu [přehled animace](animation-overview.md) a [přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
 Následující příklad ukazuje toto chování animace šířka čtyři obdélníků. Příklad:  
  
- Animuje první obdélníku s <xref:System.Windows.Media.Animation.DoubleAnimation> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost `true`.  
  
- Animuje druhý obdélníku s <xref:System.Windows.Media.Animation.DoubleAnimation> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost na výchozí hodnotu `false`.  
  
- Animuje třetí obdélníku s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> vlastnost `true`.  
  
- Animuje poslední obdélníku s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> vlastnost `false`.  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Přidání výstupní hodnoty animace do počáteční hodnoty animace](how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [Opakování animace](how-to-repeat-an-animation.md)
- [Přehled animace](animation-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy](animation-and-timing-how-to-topics.md)
