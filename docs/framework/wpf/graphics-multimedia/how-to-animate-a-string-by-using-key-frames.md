---
title: Animace řetězce pomocí klíčových snímků
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344674"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="d1e9b-102">Animace řetězce pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="d1e9b-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="d1e9b-103">Tento příklad ukazuje, jak animovat řetězec, <xref:System.Windows.Controls.ContentControl.Content%2A> který v <xref:System.Windows.Controls.Button> tomto příkladu je vlastnost ovládacího prvku, pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="d1e9b-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1e9b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1e9b-104">Example</span></span>  
 <span data-ttu-id="d1e9b-105">Následující příklad používá <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> třídu k <xref:System.Windows.Controls.ContentControl.Content%2A> animaci vlastnosti <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="d1e9b-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="d1e9b-106">Všechny klíčové snímky v tomto příkladu <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> používají instanci třídy, protože animace řetězce vytvořená pomocí klíčových snímků může používat pouze samostatné klíčové snímky.</span><span class="sxs-lookup"><span data-stu-id="d1e9b-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="d1e9b-107">Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> jako je vytvoření náhlých skoků mezi hodnotami, to znamená, že změny animace probíhají rychle a nejsou jemné.</span><span class="sxs-lookup"><span data-stu-id="d1e9b-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="d1e9b-108">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="d1e9b-108">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e9b-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1e9b-109">See also</span></span>

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [<span data-ttu-id="d1e9b-110">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="d1e9b-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="d1e9b-111">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="d1e9b-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
