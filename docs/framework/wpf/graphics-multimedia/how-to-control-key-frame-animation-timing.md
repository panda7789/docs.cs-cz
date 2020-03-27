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
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="1f4c7-102">Postupy: Řízení časování pro animace klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="1f4c7-102">How to: Control Key-Frame Animation Timing</span></span>

<span data-ttu-id="1f4c7-103">Tento příklad ukazuje, jak řídit časování klíčových snímků v rámci animace klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="1f4c7-104">Stejně jako ostatní animace mají animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> klíčových snímků vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="1f4c7-105">Kromě určení doby trvání animace je třeba určit, která část této doby trvání je přidělena každému z jejích klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="1f4c7-106">Chcete-li přidělit čas, <xref:System.Windows.Media.Animation.KeyTime> zadáte pro každý klíčový snímek v animaci.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>

<span data-ttu-id="1f4c7-107">Pro <xref:System.Windows.Media.Animation.KeyTime> každý klíčový snímek určuje, kdy klíčový snímek končí (neurčuje dobu přehrávání klíčového snímku).</span><span class="sxs-lookup"><span data-stu-id="1f4c7-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="1f4c7-108">Můžete zadat <xref:System.Windows.Media.Animation.KeyTime> hodnotu <xref:System.TimeSpan> jako hodnotu, jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> procento <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> nebo jako nebo speciální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>

## <a name="example"></a><span data-ttu-id="1f4c7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f4c7-109">Example</span></span>

<span data-ttu-id="1f4c7-110">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> k animaci obdélníku na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="1f4c7-111">Klíčové časy klíčových snímků <xref:System.TimeSpan> jsou nastaveny s hodnotami.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

<span data-ttu-id="1f4c7-112">Následující obrázek znázorňuje, když je dosaženo hodnoty každého klíčového snímku.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-112">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="1f4c7-113">![Hodnoty klíče jsou dosaženy na 3, 4 a 10 sekund](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="1f4c7-113">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>

<span data-ttu-id="1f4c7-114">Následující příklad ukazuje animaci, která je identická, s tím rozdílem, že klíčové časy klíčových snímků jsou nastaveny s procentuálními hodnotami.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

<span data-ttu-id="1f4c7-115">Následující obrázek znázorňuje, když je dosaženo hodnoty každého klíčového snímku.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-115">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="1f4c7-116">![Hodnoty klíče jsou dosaženy na 3, 4 a 10 sekund](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="1f4c7-116">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>

<span data-ttu-id="1f4c7-117">Další příklad <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> používá hodnoty času klíče.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

<span data-ttu-id="1f4c7-118">Následující obrázek znázorňuje, když je dosaženo hodnoty každého klíčového snímku.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-118">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="1f4c7-119">![Hodnoty klíče jsou dosaženy při 3,3,6,6 a 9,9 sekundy](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="1f4c7-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>

<span data-ttu-id="1f4c7-120">Poslední příklad <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> používá hodnoty času klíče.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

<span data-ttu-id="1f4c7-121">Následující obrázek znázorňuje, když je dosaženo hodnoty každého klíčového snímku.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-121">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="1f4c7-122">![Hodnoty klíče jsou dosaženy na 0, 5 a 10 sekund](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="1f4c7-122">![Key values are reached at 0, 5, and 10 seconds](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>

<span data-ttu-id="1f4c7-123">Pro jednoduchost kód verze tohoto příkladu použít místní animace, nikoli scénáře, protože pouze jedna animace se používá na jednu vlastnost, ale příklady mohou být upraveny tak, aby místo toho použít scénáře.</span><span class="sxs-lookup"><span data-stu-id="1f4c7-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="1f4c7-124">Příklad, který ukazuje, jak deklarovat scénář v kódu, najdete v [tématu Animate vlastnost pomocí storyboardu](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="1f4c7-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>

<span data-ttu-id="1f4c7-125">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="1f4c7-125">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span> <span data-ttu-id="1f4c7-126">Další informace o animacích klíčových snímků naleznete v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1f4c7-126">For more information about key frame animations, see the [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f4c7-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f4c7-127">See also</span></span>

- [<span data-ttu-id="1f4c7-128">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="1f4c7-128">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="1f4c7-129">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="1f4c7-129">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="1f4c7-130">– postupy</span><span class="sxs-lookup"><span data-stu-id="1f4c7-130">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
