---
title: 'Postupy: Otočení objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: 7eb562d81bdd8c9187672b31ed08ed6ac27da41c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561940"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="3fb67-102">Postupy: Otočení objektu</span><span class="sxs-lookup"><span data-stu-id="3fb67-102">How to: Rotate an Object</span></span>
<span data-ttu-id="3fb67-103">Tento příklad ukazuje, jak objektu.</span><span class="sxs-lookup"><span data-stu-id="3fb67-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="3fb67-104">V příkladu se nejdřív vytvoří <xref:System.Windows.Media.RotateTransform> a pak specifikuje jeho <xref:System.Windows.Media.RotateTransform.Angle%2A> ve stupních.</span><span class="sxs-lookup"><span data-stu-id="3fb67-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="3fb67-105">Následující příklad otočí <xref:System.Windows.Shapes.Polyline> objektu 45 stupňů o jeho levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="3fb67-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fb67-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fb67-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="3fb67-107"><xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> zadejte bod o tom, které se objekt otočen.</span><span class="sxs-lookup"><span data-stu-id="3fb67-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="3fb67-108">Tento bod center je vyjádřeno v prostoru souřadnic elementu, který transformuje.</span><span class="sxs-lookup"><span data-stu-id="3fb67-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="3fb67-109">Ve výchozím nastavení je oběh se použije k (0,0), který je levém horním rohu objektu k transformaci.</span><span class="sxs-lookup"><span data-stu-id="3fb67-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="3fb67-110">Další příklad otočí <xref:System.Windows.Shapes.Polyline> objektu 45 stupňů po směru hodinových ručiček kolem bodu (25,50).</span><span class="sxs-lookup"><span data-stu-id="3fb67-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="3fb67-111">Následující obrázek znázorňuje výsledky použití <xref:System.Windows.Media.Transform> na dva objekty.</span><span class="sxs-lookup"><span data-stu-id="3fb67-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="3fb67-112">![Otočení o 45 stupňů s různými středy](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="3fb67-112">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="3fb67-113">Dva objekty, které otočit 45 stupňů z různých otáčení centra</span><span class="sxs-lookup"><span data-stu-id="3fb67-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="3fb67-114"><xref:System.Windows.Shapes.Polyline> v předchozích příkladech je <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3fb67-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="3fb67-115">Pokud použijete <xref:System.Windows.Media.Transform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost <xref:System.Windows.UIElement>, můžete použít <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnosti a určit tak pro počátek každých <xref:System.Windows.Media.Transform> , můžete použít k elementu.</span><span class="sxs-lookup"><span data-stu-id="3fb67-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="3fb67-116">Protože <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost používá relativních souřadnicích, můžete použít transformaci k centru elementu i v případě, že neznáte jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="3fb67-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="3fb67-117">Další informace a příklady naleznete v tématu [zadejte počátek transformace pomocí relativní hodnoty](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="3fb67-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="3fb67-118">Kompletní příklad, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="3fb67-118">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb67-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fb67-119">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="3fb67-120">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="3fb67-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="3fb67-121">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="3fb67-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
