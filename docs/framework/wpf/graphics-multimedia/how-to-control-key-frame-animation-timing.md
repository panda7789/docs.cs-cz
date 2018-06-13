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
ms.openlocfilehash: 7aacb975557a25b8ea7a80e02c16a59b8a746e26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562287"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Postupy: Řízení časování pro animace klíčových snímků
Tento příklad ukazuje, jak řídit načasování klíčových snímků v rámci klíč rámce animace. Jako jiné animace animací jednotlivých klíče mají <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost. Kromě určení trvání animace, budete muset zadat, jaká část této hodnotě DURATION je vymezena pro každý z jeho klíčových snímků. Chcete-li přidělit čas, zadejte <xref:System.Windows.Media.Animation.KeyTime> pro každý klíčových snímků animace.  
  
 <xref:System.Windows.Media.Animation.KeyTime> u jednotlivých klíčových snímků určuje při klíče rámečku končí, (neurčuje dobu hraje klíčový snímek). Můžete zadat <xref:System.Windows.Media.Animation.KeyTime> jako <xref:System.TimeSpan> hodnotu, jako procento, nebo jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> nebo <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> speciální hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> pro animaci obdélníku po obrazovce. Klíče časy klíčových snímků se nastavují s <xref:System.TimeSpan> hodnoty.  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 Následující obrázek ukazuje, když je dosaženo hodnoty každého klíče snímku.  
  
 ![Hodnoty klíče jsou k dispozici na adrese 3, 4 a 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")  
  
 Další příklad ukazuje animace, která je stejná, s tím rozdílem, že klíče časy klíčových snímků se nastavují s procentní hodnoty.  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 Následující obrázek ukazuje, když je dosaženo hodnoty každého klíče snímku.  
  
 ![Hodnoty klíče jsou k dispozici na adrese 3, 4 a 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")  
  
 Další příklad používá <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> čas hodnoty klíče.  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 Následující obrázek ukazuje, když je dosaženo hodnoty každého klíče snímku.  
  
 ![Hodnoty klíče se dosáhne na 3.3,6.6 a 9.9 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")  
  
 Poslední příklad používá <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> čas hodnoty klíče.  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 Následující obrázek ukazuje, když je dosaženo hodnoty každého klíče snímku.  
  
 ![Hodnoty klíče jsou k dispozici na adrese 0, 5 až 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")  
  
 Pro jednoduchost verze při použití animace místní použijte tento příklad kódu není scénářů, protože se právě používá jenom jeden animace do vlastnosti jediné, ale příklady může upravit tak, aby místo toho použijte scénářů. Příkladem zobrazujícím postup deklarovat storyboard v kódu, najdete v části [animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012). Další informace o klíčových snímků animace najdete v tématu [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
