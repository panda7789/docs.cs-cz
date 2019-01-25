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
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="ccac2-102">Postupy: Řízení časování pro animace klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="ccac2-102">How to: Control Key-Frame Animation Timing</span></span>
<span data-ttu-id="ccac2-103">Tento příklad ukazuje, jak řídit načasování v rámci klíčových snímků animace klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="ccac2-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="ccac2-104">Stejně jako jiné animace klíčových snímků animace mít <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ccac2-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="ccac2-105">Kromě určení doby trvání animace, budete muset určit, jaká část tento čas je vymezena pro každý z jeho použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="ccac2-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="ccac2-106">Chcete-li přidělit čas, zadejte <xref:System.Windows.Media.Animation.KeyTime> pro každý klíčový snímek animace.</span><span class="sxs-lookup"><span data-stu-id="ccac2-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>  
  
 <span data-ttu-id="ccac2-107"><xref:System.Windows.Media.Animation.KeyTime> u každé klíčové rámečku určuje při klíčové rámečku končí (neurčuje dobu hraje klíčový snímek).</span><span class="sxs-lookup"><span data-stu-id="ccac2-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="ccac2-108">Můžete zadat <xref:System.Windows.Media.Animation.KeyTime> jako <xref:System.TimeSpan> hodnotu jako procento, nebo jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> nebo <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> zvláštní hodnota.</span><span class="sxs-lookup"><span data-stu-id="ccac2-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccac2-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccac2-109">Example</span></span>  
 <span data-ttu-id="ccac2-110">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> do animace obdélníku napříč obrazovkou.</span><span class="sxs-lookup"><span data-stu-id="ccac2-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="ccac2-111">Klíčové snímky klíče časy se nastavují s <xref:System.TimeSpan> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ccac2-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 <span data-ttu-id="ccac2-112">Následující ilustrace ukazuje po dosažení hodnotu každé klíčové rámečku.</span><span class="sxs-lookup"><span data-stu-id="ccac2-112">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="ccac2-113">![Hodnoty klíče je dostupný na adrese 3, 4 – 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="ccac2-113">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>  
  
 <span data-ttu-id="ccac2-114">Další příklad ukazuje, animace, která je stejná, s tím rozdílem, že klíče časy klíčových snímků se nastavují s procentní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ccac2-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 <span data-ttu-id="ccac2-115">Následující ilustrace ukazuje po dosažení hodnotu každé klíčové rámečku.</span><span class="sxs-lookup"><span data-stu-id="ccac2-115">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="ccac2-116">![Hodnoty klíče je dostupný na adrese 3, 4 – 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="ccac2-116">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>  
  
 <span data-ttu-id="ccac2-117">Následující příklad používá <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> času hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="ccac2-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 <span data-ttu-id="ccac2-118">Následující ilustrace ukazuje po dosažení hodnotu každé klíčové rámečku.</span><span class="sxs-lookup"><span data-stu-id="ccac2-118">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="ccac2-119">![Hodnoty klíče se dosáhne 3.3,6.6 a 9.9 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="ccac2-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>  
  
 <span data-ttu-id="ccac2-120">V posledním příkladu <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> času hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="ccac2-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 <span data-ttu-id="ccac2-121">Následující ilustrace ukazuje po dosažení hodnotu každé klíčové rámečku.</span><span class="sxs-lookup"><span data-stu-id="ccac2-121">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="ccac2-122">![Hodnoty klíče se dosáhne nastavena na 0, 5 a 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="ccac2-122">![Key values are reached at 0, 5, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>  
  
 <span data-ttu-id="ccac2-123">Pro zjednodušení verze kódu použijte místní animace tento příklad, ne scénářů, protože pouze jeden animace se zavádí jedné vlastnosti, ale příklady může upravit tak, aby místo toho použijte scénáře.</span><span class="sxs-lookup"><span data-stu-id="ccac2-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="ccac2-124">Příklad ukazuje, jak deklarovat scénáře v kódu, naleznete v tématu [animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="ccac2-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="ccac2-125">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="ccac2-125">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span> <span data-ttu-id="ccac2-126">Další informace o animacích klíčových snímků, najdete v článku [přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ccac2-126">For more information about key frame animations, see the [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccac2-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccac2-127">See also</span></span>
- [<span data-ttu-id="ccac2-128">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="ccac2-128">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="ccac2-129">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="ccac2-129">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="ccac2-130">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="ccac2-130">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
