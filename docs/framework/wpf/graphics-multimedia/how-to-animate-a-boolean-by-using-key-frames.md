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
ms.openlocfilehash: 0142748a5c8e9a4375802d1b48beec0501d37e7c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521071"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="239a5-102">Postupy: Animace logické hodnoty použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="239a5-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="239a5-103">Tento příklad ukazuje, jak animovat vlastnost typu Boolean hodnotu <xref:System.Windows.Controls.Button> ovládacího prvku s použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="239a5-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="239a5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="239a5-104">Example</span></span>  
 <span data-ttu-id="239a5-105">V následujícím příkladu <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.UIElement.IsEnabled%2A> vlastnost <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="239a5-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="239a5-106">Instance pomocí klíčových snímků v tomto příkladu <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> třídy.</span><span class="sxs-lookup"><span data-stu-id="239a5-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="239a5-107">Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> vytvoření i s náhlými přechodů mezi hodnotami, to znamená, je přehrávat nepravidelně přesun animace.</span><span class="sxs-lookup"><span data-stu-id="239a5-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="239a5-108">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="239a5-108">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239a5-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="239a5-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>  
 <xref:System.Windows.UIElement.IsEnabled%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="239a5-110">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="239a5-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="239a5-111">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="239a5-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
