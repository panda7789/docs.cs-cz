---
title: 'Postupy: Řízení časování pro animace klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344737"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Postupy: Řízení časování pro animace klíčových snímků

Tento příklad ukazuje, jak řídit časování klíčových snímků v rámci animace klíčových snímků. Stejně jako ostatní animace mají animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> klíčových snímků vlastnost. Kromě určení doby trvání animace je třeba určit, která část této doby trvání je přidělena každému z jejích klíčových snímků. Chcete-li přidělit čas, <xref:System.Windows.Media.Animation.KeyTime> zadáte pro každý klíčový snímek v animaci.

Pro <xref:System.Windows.Media.Animation.KeyTime> každý klíčový snímek určuje, kdy klíčový snímek končí (neurčuje dobu přehrávání klíčového snímku). Můžete zadat <xref:System.Windows.Media.Animation.KeyTime> hodnotu <xref:System.TimeSpan> jako hodnotu, jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> procento <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> nebo jako nebo speciální hodnotu.

## <a name="example"></a>Příklad

Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> k animaci obdélníku na obrazovce. Klíčové časy klíčových snímků <xref:System.TimeSpan> jsou nastaveny s hodnotami.

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

Následující obrázek znázorňuje, když je dosaženo hodnoty každého klíčového snímku.

![Hodnoty klíče jsou dosaženy na 3, 4 a 10 sekund](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")

Následující příklad ukazuje animaci, která je identická, s tím rozdílem, že klíčové časy klíčových snímků jsou nastaveny s procentuálními hodnotami.

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

Následující obrázek znázorňuje, když je dosaženo hodnoty každého klíčového snímku.

![Hodnoty klíče jsou dosaženy na 3, 4 a 10 sekund](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")

Další příklad <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> používá hodnoty času klíče.

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

Následující obrázek znázorňuje, když je dosaženo hodnoty každého klíčového snímku.

![Hodnoty klíče jsou dosaženy při 3,3,6,6 a 9,9 sekundy](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")

Poslední příklad <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> používá hodnoty času klíče.

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

Následující obrázek znázorňuje, když je dosaženo hodnoty každého klíčového snímku.

![Hodnoty klíče jsou dosaženy na 0, 5 a 10 sekund](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")

Pro jednoduchost kód verze tohoto příkladu použít místní animace, nikoli scénáře, protože pouze jedna animace se používá na jednu vlastnost, ale příklady mohou být upraveny tak, aby místo toho použít scénáře. Příklad, který ukazuje, jak deklarovat scénář v kódu, najdete v [tématu Animate vlastnost pomocí storyboardu](how-to-animate-a-property-by-using-a-storyboard.md).

Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation). Další informace o animacích klíčových snímků naleznete v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md).

## <a name="see-also"></a>Viz také

- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Přehled animace](animation-overview.md)
- [– postupy](animation-and-timing-how-to-topics.md)
