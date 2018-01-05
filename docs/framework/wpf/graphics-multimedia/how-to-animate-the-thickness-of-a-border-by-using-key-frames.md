---
title: "Postupy: Animace tloušťky ohraničení použitím klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f255ff38ec7ee79f02a0cd40a3f0143c36e1c58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="3f8c5-102">Postupy: Animace tloušťky ohraničení použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="3f8c5-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="3f8c5-103">Tento příklad ukazuje, jak animace <xref:System.Windows.Controls.Control.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="3f8c5-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f8c5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f8c5-104">Example</span></span>  
 <span data-ttu-id="3f8c5-105">Následující příklad používá <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Controls.Control.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="3f8c5-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="3f8c5-106">Tato animace používá tři klíčových snímků následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3f8c5-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="3f8c5-107">Při první půl sekundy používá instanci <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> třídy postupně zvyšovat Tloušťka ohraničení.</span><span class="sxs-lookup"><span data-stu-id="3f8c5-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="3f8c5-108">Tento příklad používá <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> vytvořit smooth lineární nárůst mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="3f8c5-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2.  <span data-ttu-id="3f8c5-109">Na konci další půl sekundy používá instanci <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> třída najednou zvýšit sílu ohraničení.</span><span class="sxs-lookup"><span data-stu-id="3f8c5-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="3f8c5-110">Diskrétní klíčových snímků jako ty, odvozené od <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> vytvoření nečekané přechodů mezi hodnotami, který je, je trhané přesun animace.</span><span class="sxs-lookup"><span data-stu-id="3f8c5-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3.  <span data-ttu-id="3f8c5-111">Během poslední dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> třída snížení sílu ohraničení.</span><span class="sxs-lookup"><span data-stu-id="3f8c5-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="3f8c5-112">Křivkový klíčových snímků jako ty, odvozené od <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnot <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3f8c5-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="3f8c5-113">Do tohoto klíče rámce animace spustí pomalu a urychluje exponenciálnímu ke konci čas segmentu.</span><span class="sxs-lookup"><span data-stu-id="3f8c5-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="3f8c5-114">Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="3f8c5-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8c5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f8c5-115">See Also</span></span>  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [<span data-ttu-id="3f8c5-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="3f8c5-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="3f8c5-117">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="3f8c5-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [<span data-ttu-id="3f8c5-118">Animace hodnoty BorderThickness</span><span class="sxs-lookup"><span data-stu-id="3f8c5-118">Animate a BorderThickness Value</span></span>](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
