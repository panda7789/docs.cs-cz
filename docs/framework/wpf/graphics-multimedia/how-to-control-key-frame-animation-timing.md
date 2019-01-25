---
title: 'Postupy: Řízení časování pro animace klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 3a8e11ee8bfbbe87ca5a1c51b815dd21c124a951
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712022"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Postupy: Řízení časování pro animace klíčových snímků
Tento příklad ukazuje, jak řídit načasování v rámci klíčových snímků animace klíčových snímků. Stejně jako jiné animace klíčových snímků animace mít <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost. Kromě určení doby trvání animace, budete muset určit, jaká část tento čas je vymezena pro každý z jeho použitím klíčových snímků. Chcete-li přidělit čas, zadejte <xref:System.Windows.Media.Animation.KeyTime> pro každý klíčový snímek animace.  
  
 <xref:System.Windows.Media.Animation.KeyTime> u každé klíčové rámečku určuje při klíčové rámečku končí (neurčuje dobu hraje klíčový snímek). Můžete zadat <xref:System.Windows.Media.Animation.KeyTime> jako <xref:System.TimeSpan> hodnotu jako procento, nebo jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> nebo <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> zvláštní hodnota.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> do animace obdélníku napříč obrazovkou. Klíčové snímky klíče časy se nastavují s <xref:System.TimeSpan> hodnoty.  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 Následující ilustrace ukazuje po dosažení hodnotu každé klíčové rámečku.  
  
 ![Hodnoty klíče je dostupný na adrese 3, 4 – 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")  
  
 Další příklad ukazuje, animace, která je stejná, s tím rozdílem, že klíče časy klíčových snímků se nastavují s procentní hodnoty.  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 Následující ilustrace ukazuje po dosažení hodnotu každé klíčové rámečku.  
  
 ![Hodnoty klíče je dostupný na adrese 3, 4 – 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> času hodnoty klíče.  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 Následující ilustrace ukazuje po dosažení hodnotu každé klíčové rámečku.  
  
 ![Hodnoty klíče se dosáhne 3.3,6.6 a 9.9 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")  
  
 V posledním příkladu <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> času hodnoty klíče.  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 Následující ilustrace ukazuje po dosažení hodnotu každé klíčové rámečku.  
  
 ![Hodnoty klíče se dosáhne nastavena na 0, 5 a 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")  
  
 Pro zjednodušení verze kódu použijte místní animace tento příklad, ne scénářů, protože pouze jeden animace se zavádí jedné vlastnosti, ale příklady může upravit tak, aby místo toho použijte scénáře. Příklad ukazuje, jak deklarovat scénáře v kódu, naleznete v tématu [animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012). Další informace o animacích klíčových snímků, najdete v článku [přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
## <a name="see-also"></a>Viz také:
- [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
