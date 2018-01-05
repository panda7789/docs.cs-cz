---
title: "Postupy: Řízení animací použitím polí Od, Komu a Kdo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17f87c8bcf09022aa389df779e29f5e5affabc20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Postupy: Řízení animací použitím polí Od, Komu a Kdo
"Z/do nebo By" nebo "základní animace" vytvoří přechod mezi dvě cílové hodnoty (najdete v části [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) Úvod pro různé typy animací). Pokud chcete nastavit cílové hodnoty základní animace, použijte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti.  Následující tabulka shrnuje, jak <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti mohou být použity společně nebo samostatně k určení animace cílové hodnoty.  
  
|Byly zadány vlastnosti|Výsledné chování|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Animace postupuje od hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu vlastnosti se animovaný nebo na předchozí animace výstupu hodnotu, v závislosti na tom, jak jsou nakonfigurované předchozí animace.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>a<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animace postupuje od hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu zadanou pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>a<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animace postupuje od hodnoty určené <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost na hodnotu zadanou pomocí součet <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnosti.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animace hodnoty z animovaný vlastnost základní hodnoty nebo předchozí animace výstupu hodnotu na hodnotu zadanou pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animace postupuje od základní hodnoty vlastnosti se animovaný nebo předchozí animace výstupu hodnota součtu tuto hodnotu a hodnotu zadanou pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost.|  
  
> [!NOTE]
>  Nenastavujte i <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vlastnost na stejné animace.  
  
 Pokud chcete použít jiné metody interpolace nebo animace mezi více než dvě cílové hodnoty, použijte klíčových snímků animace. V tématu [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md) Další informace.  
  
 Informace o použití více animace do vlastnosti jediné najdete v tématu [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Následující příklad ukazuje různé důsledky nastavení <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, a <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnosti animace.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Z, k a ukázkové hodnoty Target animace](http://go.microsoft.com/fwlink/?LinkID=159988)
