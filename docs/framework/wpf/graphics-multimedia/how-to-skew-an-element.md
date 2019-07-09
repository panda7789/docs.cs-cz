---
title: 'Postupy: Zkosení elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: cf770a284238826852e788e27f3b3f329ed0269f
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664089"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="82e61-102">Postupy: Zkosení elementu</span><span class="sxs-lookup"><span data-stu-id="82e61-102">How to: Skew an Element</span></span>
<span data-ttu-id="82e61-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.SkewTransform> zkosení elementu.</span><span class="sxs-lookup"><span data-stu-id="82e61-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="82e61-104">Nerovnoměrná distribuce, které se taky říká zkosení je transformace, která roztáhne souřadnicového prostoru nerovnoměrné způsobem.</span><span class="sxs-lookup"><span data-stu-id="82e61-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="82e61-105">Jeden typické použití <xref:System.Windows.Media.SkewTransform> je pro simulaci 3D hloubka v 2D objekty.</span><span class="sxs-lookup"><span data-stu-id="82e61-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3-D depth in 2-D objects.</span></span>  
  
 <span data-ttu-id="82e61-106">Použití <xref:System.Windows.Media.SkewTransform.CenterX%2A> a <xref:System.Windows.Media.SkewTransform.CenterY%2A> vlastnosti k určení centru bod <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="82e61-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="82e61-107">Použití <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A> vlastnosti k určení nerovnoměrné rozdělení úhlu z osy x a y a zkosení aktuální systém souřadnic spolu tyto osy.</span><span class="sxs-lookup"><span data-stu-id="82e61-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="82e61-108">Chcete-li odhadnout účinky transformaci zkosení, zvažte, který <xref:System.Windows.Media.SkewTransform.AngleX%2A> zkosí hodnoty na ose x vzhledem k původní systém souřadnic.</span><span class="sxs-lookup"><span data-stu-id="82e61-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="82e61-109">Proto se pro <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, osy y otočí 30 stupňů prostřednictvím původ a zkosí hodnoty x – o 30 stupňů z tohoto počátku.</span><span class="sxs-lookup"><span data-stu-id="82e61-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="82e61-110">Podobně <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 zkosí hodnot y tvaru o 30 stupňů z původního zdroje.</span><span class="sxs-lookup"><span data-stu-id="82e61-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="82e61-111">Všimněte si, že to není stejný účinek jako překladu (přesun) souřadnicový systém o 30 stupňů x nebo y.</span><span class="sxs-lookup"><span data-stu-id="82e61-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="82e61-112">Následující příklad použije vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (0; 0).</span><span class="sxs-lookup"><span data-stu-id="82e61-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82e61-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="82e61-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="82e61-114">Následující příklad použije vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (25,25).</span><span class="sxs-lookup"><span data-stu-id="82e61-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="82e61-115">Následující příklad použije svislé zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (25,25).</span><span class="sxs-lookup"><span data-stu-id="82e61-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="82e61-116">Následující obrázek znázorňuje různé nerovnoměrné distribuce, které se používají v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="82e61-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="82e61-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="82e61-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="82e61-118">Tři SkewTransform – příklady jsou znázorněné</span><span class="sxs-lookup"><span data-stu-id="82e61-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="82e61-119">Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="82e61-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e61-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82e61-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="82e61-121">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="82e61-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="82e61-122">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="82e61-122">How-to Topics</span></span>](transformations-how-to-topics.md)
