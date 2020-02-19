---
title: 'Postupy: Řízení animací použitím polí Od, Komu a Kdo'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: b06df97dc57c58a01f30be2d70bfeebf104521ad
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451782"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Postupy: Řízení animací použitím polí Od, Komu a Kdo
"Od/do/" nebo "základní animace" vytvoří přechod mezi dvěma cílovými hodnotami (viz [Přehled animace](animation-overview.md) pro Úvod k různým typům animací). Chcete-li nastavit cílové hodnoty základní animace, použijte její <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>a vlastnosti <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  Následující tabulka shrnuje, jak lze pomocí vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> použít společně nebo samostatně k určení cílových hodnot animace.  
  
|Zadané vlastnosti|Výsledné chování|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Animace pokračuje z hodnoty určené vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> na základní hodnotu vlastnosti Animated nebo na výstupní hodnotu předchozí animace v závislosti na tom, jak je nakonfigurované předchozí animace.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animace pokračuje z hodnoty určené vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> na hodnotu určenou vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animace pokračuje z hodnoty určené vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> na hodnotu určenou součtem vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animace pokračuje od základní hodnoty animované vlastnosti nebo z výstupní hodnoty předchozí animace s hodnotou určenou vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animace pokračuje od základní hodnoty vlastnosti Animated nebo z výstupní hodnoty předchozí animace k součtu hodnoty a hodnoty určené vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.|  
  
> [!NOTE]
> Nenastavujte vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> a vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> u stejné animace.  
  
 Chcete-li použít jiné metody interpolace nebo animovat mezi více než dvěma cílovými hodnotami, použijte animaci klíčových snímků. Další informace najdete v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md) .  
  
 Informace o použití více animací pro jednu vlastnost najdete v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
 Následující příklad ukazuje různé účinky nastavení vlastností <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> na animace.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Ukázka cílových hodnot z, do a podle animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
