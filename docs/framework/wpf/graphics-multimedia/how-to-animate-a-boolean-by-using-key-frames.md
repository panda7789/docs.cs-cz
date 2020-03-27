---
title: 'Postupy: Animace logické hodnoty použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 35704996dcf21fe463169dc13572941bcd8fbad1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344946"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="0e022-102">Postupy: Animace logické hodnoty použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="0e022-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="0e022-103">Tento příklad ukazuje, jak animovat hodnotu logické vlastnosti <xref:System.Windows.Controls.Button> ovládacího prvku pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="0e022-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e022-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e022-104">Example</span></span>  
 <span data-ttu-id="0e022-105">Následující příklad používá <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> třídu k <xref:System.Windows.UIElement.IsEnabled%2A> animaci vlastnosti ovládacího <xref:System.Windows.Controls.Button> prvku.</span><span class="sxs-lookup"><span data-stu-id="0e022-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="0e022-106">Všechny klíčové snímky v tomto příkladu <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> používají instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="0e022-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="0e022-107">Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> jako je vytvoření náhlých skoků mezi hodnotami, to znamená, že pohyb animace je trhaný.</span><span class="sxs-lookup"><span data-stu-id="0e022-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="0e022-108">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="0e022-108">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e022-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e022-109">See also</span></span>

- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [<span data-ttu-id="0e022-110">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="0e022-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="0e022-111">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="0e022-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
