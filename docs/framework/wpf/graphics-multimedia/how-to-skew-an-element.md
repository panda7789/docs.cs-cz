---
title: 'Postupy: Zkreslení elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 8bd860a71253a55cb3148426dbb61cbd3477e95e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561560"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="6ca98-102">Postupy: Zkreslení elementu</span><span class="sxs-lookup"><span data-stu-id="6ca98-102">How to: Skew an Element</span></span>
<span data-ttu-id="6ca98-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.SkewTransform> zkosení elementu.</span><span class="sxs-lookup"><span data-stu-id="6ca98-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="6ca98-104">Zkosení, která je také označována jako zkosení, je transformaci, která roztahovány souřadnicového prostoru neuniformní způsobem.</span><span class="sxs-lookup"><span data-stu-id="6ca98-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="6ca98-105">Jeden typické použití <xref:System.Windows.Media.SkewTransform> je pro simulaci [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] podrobně [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="6ca98-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="6ca98-106">Použití <xref:System.Windows.Media.SkewTransform.CenterX%2A> a <xref:System.Windows.Media.SkewTransform.CenterY%2A> vlastnosti k určení centru bodu služby <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="6ca98-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="6ca98-107">Použití <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A> vlastnosti k určení zkosení úhel osy x a y a zkosení podél tyto OS aktuální souřadnicový systém.</span><span class="sxs-lookup"><span data-stu-id="6ca98-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="6ca98-108">K předvídání účinku transformaci zkosení, zvažte, které <xref:System.Windows.Media.SkewTransform.AngleX%2A> zkosí hodnoty osy x vzhledem k původní souřadnicový systém.</span><span class="sxs-lookup"><span data-stu-id="6ca98-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="6ca98-109">Proto pro <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, osy y otočí 30 stupňů prostřednictvím počátku a zkosí hodnoty v x-o 30 stupňů z tohoto počátku.</span><span class="sxs-lookup"><span data-stu-id="6ca98-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="6ca98-110">Podobně <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 zkosí hodnot y tvaru o 30 stupňů z tohoto počátku.</span><span class="sxs-lookup"><span data-stu-id="6ca98-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="6ca98-111">Všimněte si, že to není stejného efektu jako překladu (přesunutí) souřadnicový systém o 30 stupňů v x - nebo y-.</span><span class="sxs-lookup"><span data-stu-id="6ca98-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="6ca98-112">Následující příklad se vztahuje vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> z bodu center (0,0).</span><span class="sxs-lookup"><span data-stu-id="6ca98-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ca98-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ca98-113">Example</span></span>  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="6ca98-114">Následující příklad se vztahuje vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> z středový bod (25,25).</span><span class="sxs-lookup"><span data-stu-id="6ca98-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="6ca98-115">Následující příklad se vztahuje svislé zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> z středový bod (25,25).</span><span class="sxs-lookup"><span data-stu-id="6ca98-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="6ca98-116">Následující obrázek ukazuje různé zkosí, které se používají v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="6ca98-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="6ca98-117">![Příklady SkewTransform –](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="6ca98-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="6ca98-118">Tři SkewTransform – příklady jsou znázorněné</span><span class="sxs-lookup"><span data-stu-id="6ca98-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="6ca98-119">Kompletní příklad, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="6ca98-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca98-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ca98-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [<span data-ttu-id="6ca98-121">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="6ca98-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="6ca98-122">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="6ca98-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
