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
ms.openlocfilehash: d1c4700a5dc8f6ed99043552999d8f014116da8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189639"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="6aa0e-102">Postupy: Otočení objektu</span><span class="sxs-lookup"><span data-stu-id="6aa0e-102">How to: Rotate an Object</span></span>
<span data-ttu-id="6aa0e-103">Tento příklad ukazuje, jak otočení objektu.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="6aa0e-104">V příkladu se nejdřív vytvoří <xref:System.Windows.Media.RotateTransform> a určuje jeho <xref:System.Windows.Media.RotateTransform.Angle%2A> ve stupních.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="6aa0e-105">V následujícím příkladu se otočí <xref:System.Windows.Shapes.Polyline> objektu 45 stupňů o jeho levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aa0e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6aa0e-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="6aa0e-107"><xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> určete bod, o tom, které je objekt otočen.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="6aa0e-108">Tato středový bod je vyjádřen v souřadnicového prostoru elementu, který je transformovat.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="6aa0e-109">Ve výchozím nastavení otočení platí pro (0; 0), což je levého horního rohu objekt, který má transformovat.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="6aa0e-110">Následující příklad otočí <xref:System.Windows.Shapes.Polyline> objektu 45 stupňů po směru hodinových ručiček kolem bodu (25,50).</span><span class="sxs-lookup"><span data-stu-id="6aa0e-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="6aa0e-111">Následující obrázek znázorňuje výsledkem použití <xref:System.Windows.Media.Transform> dvěma objekty.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="6aa0e-112">![45 stupňů rotace s různými středy](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="6aa0e-112">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="6aa0e-113">Dva objekty, které otáčet 45 stupňů z různých rotačních centra</span><span class="sxs-lookup"><span data-stu-id="6aa0e-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="6aa0e-114"><xref:System.Windows.Shapes.Polyline> v předchozích příkladech je <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="6aa0e-115">Při použití <xref:System.Windows.Media.Transform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost <xref:System.Windows.UIElement>, můžete použít <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnosti a určit původ pro každý <xref:System.Windows.Media.Transform> , která se vztahují na prvek.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="6aa0e-116">Vzhledem k tomu, <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost relativních souřadnic, center elementu, který můžete využít transformace, i, pokud neznáte jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="6aa0e-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="6aa0e-117">Další informace a příklad najdete v tématu [určení počátku transformace použitím relativní hodnoty](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="6aa0e-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="6aa0e-118">Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="6aa0e-118">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa0e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6aa0e-119">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="6aa0e-120">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="6aa0e-120">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="6aa0e-121">– postupy</span><span class="sxs-lookup"><span data-stu-id="6aa0e-121">How-to Topics</span></span>](transformations-how-to-topics.md)
