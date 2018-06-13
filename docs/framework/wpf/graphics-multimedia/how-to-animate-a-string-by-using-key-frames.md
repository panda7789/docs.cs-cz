---
title: Animace řetězce pomocí klíčových snímků
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 5219ce11667c84d3ceca380d5a4ddd52695736b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561056"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="4c66d-102">Animace řetězce pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="4c66d-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="4c66d-103">Tento příklad ukazuje, jak animace řetězec, který je v tomto příkladu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button> ovládacího prvku pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="4c66d-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c66d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c66d-104">Example</span></span>  
 <span data-ttu-id="4c66d-105">Následující příklad používá <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="4c66d-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="4c66d-106">Všechny klíče rámce v tomto příkladu použít instanci systému <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> třídy protože animace řetězec, který je vytvořen s klíčových snímků lze použít pouze diskrétní klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="4c66d-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="4c66d-107">Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> vytvoření nečekané přechodů mezi hodnotami, který je, změny animace dojít rychle a nejsou jemně.</span><span class="sxs-lookup"><span data-stu-id="4c66d-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="4c66d-108">Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="4c66d-108">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c66d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c66d-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.ContentControl.Content%2A>  
 <xref:System.Windows.Controls.Button>  
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>  
 [<span data-ttu-id="4c66d-110">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="4c66d-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="4c66d-111">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="4c66d-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
