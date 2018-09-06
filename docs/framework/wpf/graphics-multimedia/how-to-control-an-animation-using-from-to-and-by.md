---
title: 'Postupy: Řízení animací použitím polí Od, Komu a Kdo'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: e422c008ae3051ecd69b3278eb05fc0e2d1b1a0b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858802"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Postupy: Řízení animací použitím polí Od, Komu a Kdo
"Od/Komu/kým" nebo "základní animace" vytvoří přechod mezi dvě cílové hodnoty (naleznete v tématu [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) s úvodem do různé typy animací). Chcete-li nastavit cílové hodnoty základní animace, použijte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti.  Následující tabulka shrnuje, jak <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti mohou být použity společně nebo samostatně k určení cílové animace hodnoty.  
  
|Byly zadány vlastnosti|Výsledné chování|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Animace průběhu z hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost základní hodnotou animované vlastnosti nebo předchozí animace výstupní hodnoty v závislosti na konfiguraci předchozí animace.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animace průběhu z hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu zadanou proměnnou <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animace průběhu z hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu zadanou pomocí součtu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animace postupuje od základní hodnotou animované vlastnosti nebo předchozí animace výstupní hodnota, která má hodnotu určenou <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animace postupuje od základní hodnotou animované vlastnosti nebo předchozí animace výstupní hodnotu na součet dané hodnoty a hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost.|  
  
> [!NOTE]
>  Nenastavujte i <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost u stejného animace.  
  
 Pokud chcete použít jiné metody interpolace nebo mezi více než dva cílových hodnot animace, použijte animace klíčových snímků. Zobrazit [přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md) Další informace.  
  
 Informace o použití více animace do vlastnosti jediné najdete v tématu [přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Následující příklad ukazuje různé účinky nastavení <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnosti animace.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Od, Komu a kdo ukázkové cílové hodnoty animace](https://go.microsoft.com/fwlink/?LinkID=159988)
