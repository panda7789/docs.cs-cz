---
title: 'Postupy: Zkreslení elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: f828e4d4e59fa5ed31f81f3e83570a25add19e01
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734900"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="c0c1c-102">Postupy: Zkreslení elementu</span><span class="sxs-lookup"><span data-stu-id="c0c1c-102">How to: Skew an Element</span></span>
<span data-ttu-id="c0c1c-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.SkewTransform> zkosení elementu.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="c0c1c-104">Nerovnoměrná distribuce, které se taky říká zkosení je transformace, která roztáhne souřadnicového prostoru nerovnoměrné způsobem.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="c0c1c-105">Jeden typické použití <xref:System.Windows.Media.SkewTransform> je pro simulaci [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] hloubka v [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="c0c1c-106">Použití <xref:System.Windows.Media.SkewTransform.CenterX%2A> a <xref:System.Windows.Media.SkewTransform.CenterY%2A> vlastnosti k určení centru bod <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="c0c1c-107">Použití <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A> vlastnosti k určení nerovnoměrné rozdělení úhlu z osy x a y a zkosení aktuální systém souřadnic spolu tyto osy.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="c0c1c-108">Chcete-li odhadnout účinky transformaci zkosení, zvažte, který <xref:System.Windows.Media.SkewTransform.AngleX%2A> zkosí hodnoty na ose x vzhledem k původní systém souřadnic.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="c0c1c-109">Proto se pro <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, osy y otočí 30 stupňů prostřednictvím původ a zkosí hodnoty x – o 30 stupňů z tohoto počátku.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="c0c1c-110">Podobně <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 zkosí hodnot y tvaru o 30 stupňů z původního zdroje.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="c0c1c-111">Všimněte si, že to není stejný účinek jako překladu (přesun) souřadnicový systém o 30 stupňů x nebo y.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="c0c1c-112">Následující příklad použije vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (0; 0).</span><span class="sxs-lookup"><span data-stu-id="c0c1c-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0c1c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0c1c-113">Example</span></span>  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="c0c1c-114">Následující příklad použije vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (25,25).</span><span class="sxs-lookup"><span data-stu-id="c0c1c-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="c0c1c-115">Následující příklad použije svislé zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (25,25).</span><span class="sxs-lookup"><span data-stu-id="c0c1c-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="c0c1c-116">Následující obrázek znázorňuje různé nerovnoměrné distribuce, které se používají v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="c0c1c-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="c0c1c-117">![SkewTransform – příklady](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="c0c1c-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="c0c1c-118">Tři SkewTransform – příklady jsou znázorněné</span><span class="sxs-lookup"><span data-stu-id="c0c1c-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="c0c1c-119">Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="c0c1c-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c1c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0c1c-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [<span data-ttu-id="c0c1c-121">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="c0c1c-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="c0c1c-122">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="c0c1c-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
