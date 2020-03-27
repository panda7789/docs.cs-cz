---
title: 'Postupy: Animace objektu použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344706"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="a601c-102">Postupy: Animace objektu použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="a601c-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="a601c-103">Tento příklad ukazuje, jak animovat objekt, <xref:System.Windows.Controls.Page.Background%2A> který v <xref:System.Windows.Controls.Page> tomto příkladu je vlastností ovládacího prvku pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="a601c-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a601c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a601c-104">Example</span></span>  
 <span data-ttu-id="a601c-105">Následující příklad používá <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídu k animaci změn barev pro <xref:System.Windows.Controls.Page.Background%2A> vlastnost ovládacího <xref:System.Windows.Controls.Page> prvku.</span><span class="sxs-lookup"><span data-stu-id="a601c-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="a601c-106">Ukázková animace se v pravidelných intervalech změní na jiný štětec na pozadí.</span><span class="sxs-lookup"><span data-stu-id="a601c-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="a601c-107">Tato animace <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> používá třídu k vytvoření tří různých klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="a601c-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="a601c-108">Animace používá klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a601c-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="a601c-109">Na konci první sekundy animuje instanci třídy. <xref:System.Windows.Media.LinearGradientBrush></span><span class="sxs-lookup"><span data-stu-id="a601c-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="a601c-110">Tato část příkladu aplikuje na barvu pozadí lineární přechod tak, aby barva přecházela ze žluté na oranžovou na červenou.</span><span class="sxs-lookup"><span data-stu-id="a601c-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="a601c-111">Na konci další sekundy animuje instanci třídy. <xref:System.Windows.Media.RadialGradientBrush></span><span class="sxs-lookup"><span data-stu-id="a601c-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="a601c-112">Tato část příkladu aplikuje na barvu pozadí kruhový přechod radiálního přechodu tak, aby se barva přecházela z bílé na modrou na černou.</span><span class="sxs-lookup"><span data-stu-id="a601c-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="a601c-113">Na konci třetí sekundy animuje instanci třídy. <xref:System.Windows.Media.DrawingBrush></span><span class="sxs-lookup"><span data-stu-id="a601c-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="a601c-114">Tato část příkladu použije šachovna vzor na pozadí.</span><span class="sxs-lookup"><span data-stu-id="a601c-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="a601c-115">Animace začíná znovu a opakuje se neomezeně dlouho.</span><span class="sxs-lookup"><span data-stu-id="a601c-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a601c-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>je jediný typ klíčového snímku, který <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> můžete použít s třídou.</span><span class="sxs-lookup"><span data-stu-id="a601c-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="a601c-117">Klíčové snímky, jako <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> je vytvoření náhlých změn hodnot, to znamená, že změny barev v tomto příkladu nastanou náhle.</span><span class="sxs-lookup"><span data-stu-id="a601c-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a601c-118">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="a601c-118">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a601c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a601c-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="a601c-120">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="a601c-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="a601c-121">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="a601c-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
