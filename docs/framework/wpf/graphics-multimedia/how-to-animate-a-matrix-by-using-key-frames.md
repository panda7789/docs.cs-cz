---
title: "Postupy: Animace matice použitím klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 862e1afdcd823181dff0948fab43b1656b85f721
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="a7e7b-102">Postupy: Animace matice použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="a7e7b-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="a7e7b-103">Tento příklad ukazuje, jak animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform> pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7e7b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7e7b-104">Example</span></span>  
 <span data-ttu-id="a7e7b-105">Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="a7e7b-106">V příkladu se používá <xref:System.Windows.Media.MatrixTransform> objektu k transformaci vzhledu a umístění <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="a7e7b-107">Používá tento animace <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> třídy pro vytvoření dvou klíčových snímků a provede následující akce s nimi:</span><span class="sxs-lookup"><span data-stu-id="a7e7b-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1.  <span data-ttu-id="a7e7b-108">Animuje první <xref:System.Windows.Media.Matrix> během prvních 0,2 sekund.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="a7e7b-109">Příklad změny <xref:System.Windows.Media.Matrix.M11%2A> a <xref:System.Windows.Media.Matrix.M12%2A> vlastnosti <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="a7e7b-110">Tato změna způsobí, že tlačítko roztažení a stát nesouměrně rozdělí.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="a7e7b-111">Tento příklad také změní <xref:System.Windows.Media.Matrix.OffsetX%2A> a <xref:System.Windows.Media.Matrix.OffsetY%2A> vlastnosti tak, aby tlačítko změní pozici.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2.  <span data-ttu-id="a7e7b-112">Animuje druhý <xref:System.Windows.Media.Matrix> v 1.0 sekund.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="a7e7b-113">Tlačítko přesune na jinou pracovní pozici, zatímco tlačítko už nesouměrně rozdělí nebo roztažená.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3.  <span data-ttu-id="a7e7b-114">Animace opakuje bez omezení.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7e7b-115">Klíčové snímky, které jsou odvozeny od <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objekt vytvoření nečekané přechodů mezi hodnotami, to znamená, že je trhané přesun animace.</span><span class="sxs-lookup"><span data-stu-id="a7e7b-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a7e7b-116">Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="a7e7b-116">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e7b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7e7b-117">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [<span data-ttu-id="a7e7b-118">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="a7e7b-118">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="a7e7b-119">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="a7e7b-119">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
