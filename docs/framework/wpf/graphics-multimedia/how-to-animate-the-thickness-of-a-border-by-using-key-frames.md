---
title: 'Postupy: Animace tloušťky ohraničení použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: d30e414dd83e596da6415cc455c599820a22f3e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689952"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="cd4d2-102">Postupy: Animace tloušťky ohraničení použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="cd4d2-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="cd4d2-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Controls.Control.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd4d2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd4d2-104">Example</span></span>  
 <span data-ttu-id="cd4d2-105">V následujícím příkladu <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Controls.Control.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="cd4d2-106">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="cd4d2-107">Během prvního půl sekundy, používá instanci <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> třídy postupně zvyšovat tloušťku ohraničení.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="cd4d2-108">V příkladu <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> k vytvoření hladkého lineární zvýšení mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2.  <span data-ttu-id="cd4d2-109">Na konci další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> třídy prudce zvýšit tloušťku ohraničení.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="cd4d2-110">Diskrétní klíčových snímků jako odvozený od <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> vytvoření i s náhlými přechodů mezi hodnotami, to znamená, je přehrávat nepravidelně přesun animace.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3.  <span data-ttu-id="cd4d2-111">Během poslední dvě sekundy, používá instanci <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> třídy snížení tloušťku ohraničení.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="cd4d2-112">Klíčové snímky SpLine podobné těm odvozený od <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="cd4d2-113">V této klíčový snímek animace začíná pomalé a zrychluje exponenciálně na konci časového úseku.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="cd4d2-114">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="cd4d2-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd4d2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-115">See also</span></span>
- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="cd4d2-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="cd4d2-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="cd4d2-117">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="cd4d2-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="cd4d2-118">Animace hodnoty BorderThickness</span><span class="sxs-lookup"><span data-stu-id="cd4d2-118">Animate a BorderThickness Value</span></span>](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
