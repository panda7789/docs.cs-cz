---
title: 'Postupy: Animace matice pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963028"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="ee678-102">Postupy: Animace matice pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="ee678-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="ee678-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost s <xref:System.Windows.Media.MatrixTransform> použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="ee678-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee678-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee678-104">Example</span></span>  
 <span data-ttu-id="ee678-105">Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animaci vlastnosti <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="ee678-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="ee678-106">Příklad používá <xref:System.Windows.Media.MatrixTransform> objekt k transformaci vzhledu a pozice <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="ee678-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="ee678-107">Tato animace používá <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> třídu k vytvoření dvou klíčových snímků a s nimi provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="ee678-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="ee678-108">Animuje první <xref:System.Windows.Media.Matrix> během prvních 0,2 sekund.</span><span class="sxs-lookup"><span data-stu-id="ee678-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="ee678-109">V příkladu se změní <xref:System.Windows.Media.Matrix.M11%2A> vlastnosti <xref:System.Windows.Media.Matrix.M12%2A> <xref:System.Windows.Media.Matrix>a.</span><span class="sxs-lookup"><span data-stu-id="ee678-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="ee678-110">Tato změna způsobí, že se tlačítko roztáhne a bude zkosený.</span><span class="sxs-lookup"><span data-stu-id="ee678-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="ee678-111">V příkladu se také změní <xref:System.Windows.Media.Matrix.OffsetX%2A> vlastnosti <xref:System.Windows.Media.Matrix.OffsetY%2A> a tak, aby tlačítko změnilo pozici.</span><span class="sxs-lookup"><span data-stu-id="ee678-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="ee678-112">Animuje druhý <xref:System.Windows.Media.Matrix> v 1,0 sekund.</span><span class="sxs-lookup"><span data-stu-id="ee678-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="ee678-113">Tlačítko se přesune na jinou pozici, zatímco tlačítko již není zkosený nebo roztaženo.</span><span class="sxs-lookup"><span data-stu-id="ee678-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="ee678-114">Opakuje animaci po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="ee678-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee678-115">Klíčové snímky, které jsou odvozeny z <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objektu vytvořit náhlé přechody mezi hodnotami, tedy pohyb animace je Jerky.</span><span class="sxs-lookup"><span data-stu-id="ee678-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="ee678-116">Úplnou ukázku najdete v tématu [Ukázka animace klíčových snímků](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="ee678-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee678-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee678-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="ee678-118">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="ee678-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="ee678-119">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="ee678-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
