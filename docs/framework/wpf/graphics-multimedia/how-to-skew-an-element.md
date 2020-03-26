---
title: 'Postupy: Zkreslení elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 10b00044c1c518641281e2e72cdb5a68474b5170
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112021"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="59f45-102">Postupy: Zkreslení elementu</span><span class="sxs-lookup"><span data-stu-id="59f45-102">How to: Skew an Element</span></span>
<span data-ttu-id="59f45-103">Tento příklad ukazuje, <xref:System.Windows.Media.SkewTransform> jak použít zkosení prvku.</span><span class="sxs-lookup"><span data-stu-id="59f45-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="59f45-104">Zkosení, které je také známé jako zkosení, je transformace, která roztáhne souřadnicový prostor nerovnoměrným způsobem.</span><span class="sxs-lookup"><span data-stu-id="59f45-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="59f45-105">Jedním z typických použití a <xref:System.Windows.Media.SkewTransform> je simulace 3D hloubky ve 2D objektech.</span><span class="sxs-lookup"><span data-stu-id="59f45-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3D depth in 2D objects.</span></span>  
  
 <span data-ttu-id="59f45-106">Pomocí <xref:System.Windows.Media.SkewTransform.CenterX%2A> vlastností a <xref:System.Windows.Media.SkewTransform.CenterY%2A> určete středový bod <xref:System.Windows.Media.SkewTransform>rozhraní .</span><span class="sxs-lookup"><span data-stu-id="59f45-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="59f45-107">Pomocí <xref:System.Windows.Media.SkewTransform.AngleX%2A> vlastností a <xref:System.Windows.Media.SkewTransform.AngleY%2A> určete úhel zkosení osy x a osy y a zkosení aktuálního souřadnicového systému podél těchto os.</span><span class="sxs-lookup"><span data-stu-id="59f45-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="59f45-108">Chcete-li předpovědět efekt transformace zkosení, zvažte, že <xref:System.Windows.Media.SkewTransform.AngleX%2A> zkosí hodnoty osy x vzhledem k původnímu souřadnicovému systému.</span><span class="sxs-lookup"><span data-stu-id="59f45-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="59f45-109">Proto pro <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30 ose y otočí 30 stupňů přes počátek a zkosí hodnoty v x- o 30 stupňů od tohoto počátku.</span><span class="sxs-lookup"><span data-stu-id="59f45-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="59f45-110">Podobně 30 <xref:System.Windows.Media.SkewTransform.AngleY%2A> zkosí hodnoty y- tvaru o 30 stupňů od počátku.</span><span class="sxs-lookup"><span data-stu-id="59f45-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="59f45-111">Všimněte si, že to není stejný efekt jako překlad (přesunutí) souřadnicový systém o 30 stupňů v x- nebo y-.</span><span class="sxs-lookup"><span data-stu-id="59f45-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="59f45-112">Následující příklad použije vodorovné zkosení <xref:System.Windows.Shapes.Rectangle> o 45 stupňů na středový bod (0,0).</span><span class="sxs-lookup"><span data-stu-id="59f45-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59f45-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="59f45-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="59f45-114">Následující příklad použije vodorovné zkosení <xref:System.Windows.Shapes.Rectangle> o 45 stupňů na středový bod (25,25).</span><span class="sxs-lookup"><span data-stu-id="59f45-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="59f45-115">Následující příklad použije svislé zkosení o 45 stupňů na <xref:System.Windows.Shapes.Rectangle> středový bod (25,25).</span><span class="sxs-lookup"><span data-stu-id="59f45-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="59f45-116">Následující obrázek znázorňuje různé zkosení, které se používají v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="59f45-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="59f45-117">![Příklady SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="59f45-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="59f45-118">Tři příklady SkewTransform ilustrované</span><span class="sxs-lookup"><span data-stu-id="59f45-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="59f45-119">Kompletní ukázku naleznete v tématu [2D transformace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="59f45-119">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f45-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="59f45-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="59f45-121">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="59f45-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="59f45-122">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="59f45-122">How-to Topics</span></span>](transformations-how-to-topics.md)
