---
title: 'Postupy: Řízení animací pomocí polí Od, Komu a Kdo'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 812217a2905671567271687b974a435dd85cea47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930088"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Postupy: Řízení animací pomocí polí Od, Komu a Kdo
"Od/do/" nebo "základní animace" vytvoří přechod mezi dvěma cílovými hodnotami (viz [Přehled animace](animation-overview.md) pro Úvod k různým typům animací). K nastavení cílových hodnot základní animace použijte své <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>vlastnosti, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> .  Následující tabulka shrnuje <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, jak lze vlastnosti, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> použít společně nebo samostatně k určení cílových hodnot animace.  
  
|Zadané vlastnosti|Výsledné chování|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Animace pokračuje z hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastností na základní hodnotu vlastnosti Animated nebo na výstupní hodnotu předchozí animace v závislosti na tom, jak je nakonfigurované předchozí animace.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animace pokračuje z hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastností na hodnotu určenou <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastností.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animace pokračuje z hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastností na hodnotu určenou součtem <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastností a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> .|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animace pokračuje od základní hodnoty animované vlastnosti nebo z výstupní hodnoty předchozí animace s hodnotou určenou <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastností.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animace pokračuje od základní hodnoty vlastnosti Animated nebo z výstupní hodnoty předchozí animace k součtu hodnoty a hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastností.|  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> Nenastavujte vlastnost<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> i vlastnost ve stejné animaci.  
  
 Chcete-li použít jiné metody interpolace nebo animovat mezi více než dvěma cílovými hodnotami, použijte animaci klíčových snímků. Další informace najdete v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md) .  
  
 Informace o použití více animací pro jednu vlastnost najdete v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
 Následující příklad ukazuje různé účinky nastavení <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastností na animacích.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Ukázka cílových hodnot z, do a podle animace](https://go.microsoft.com/fwlink/?LinkID=159988)
