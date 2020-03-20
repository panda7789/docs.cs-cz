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
ms.openlocfilehash: 02d8144c28b7a4e54fb86fea5abb694cf7af34af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185969"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="0aa2b-102">Postupy: Otočení objektu</span><span class="sxs-lookup"><span data-stu-id="0aa2b-102">How to: Rotate an Object</span></span>
<span data-ttu-id="0aa2b-103">Tento příklad ukazuje, jak otočit objekt.</span><span class="sxs-lookup"><span data-stu-id="0aa2b-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="0aa2b-104">Příklad nejprve <xref:System.Windows.Media.RotateTransform> vytvoří a pak <xref:System.Windows.Media.RotateTransform.Angle%2A> určuje jeho ve stupních.</span><span class="sxs-lookup"><span data-stu-id="0aa2b-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="0aa2b-105">Následující příklad otočí <xref:System.Windows.Shapes.Polyline> objekt o 45 stupňů kolem levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="0aa2b-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0aa2b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0aa2b-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="0aa2b-107"><xref:System.Windows.Media.RotateTransform.CenterX%2A> Vlastnosti <xref:System.Windows.Media.RotateTransform.CenterY%2A> a <xref:System.Windows.Media.RotateTransform> určete bod, ve kterém je objekt otočen.</span><span class="sxs-lookup"><span data-stu-id="0aa2b-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="0aa2b-108">Tento středový bod je vyjádřen v souřadnicovém prostoru prvku, který je transformován.</span><span class="sxs-lookup"><span data-stu-id="0aa2b-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="0aa2b-109">Ve výchozím nastavení je otočení aplikováno na (0,0), což je levý horní roh objektu, který má být transformován.</span><span class="sxs-lookup"><span data-stu-id="0aa2b-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="0aa2b-110">Další příklad otočí <xref:System.Windows.Shapes.Polyline> objekt ve směru hodinových ručiček o 45 stupňů kolem bodu (25,50).</span><span class="sxs-lookup"><span data-stu-id="0aa2b-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="0aa2b-111">Následující obrázek znázorňuje <xref:System.Windows.Media.Transform> výsledky použití a na dva objekty.</span><span class="sxs-lookup"><span data-stu-id="0aa2b-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="0aa2b-112">![Otočení o 45 stupňů s různými středovými body](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="0aa2b-112">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="0aa2b-113">Dva objekty, které se otáčejí o 45 stupňů od různých rotačních středů</span><span class="sxs-lookup"><span data-stu-id="0aa2b-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="0aa2b-114">V <xref:System.Windows.Shapes.Polyline> předchozích příkladech <xref:System.Windows.UIElement>je .</span><span class="sxs-lookup"><span data-stu-id="0aa2b-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="0aa2b-115">Při použití <xref:System.Windows.Media.Transform> <xref:System.Windows.UIElement.RenderTransform%2A> vlastnosti <xref:System.Windows.UIElement>, můžete použít <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost k určení původu <xref:System.Windows.Media.Transform> pro každý, který použijete na prvek.</span><span class="sxs-lookup"><span data-stu-id="0aa2b-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="0aa2b-116">Vzhledem <xref:System.Windows.UIElement.RenderTransformOrigin%2A> k tomu, že vlastnost používá relativní souřadnice, můžete použít transformaci na střed prvku i v případě, že neznáte jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="0aa2b-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="0aa2b-117">Další informace a příklad [najdete v tématu Určení počátku transformace pomocí relativních hodnot](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="0aa2b-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="0aa2b-118">Kompletní ukázku naleznete v [tématu Ukázka 2D transformací](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="0aa2b-118">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa2b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0aa2b-119">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="0aa2b-120">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="0aa2b-120">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="0aa2b-121">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="0aa2b-121">How-to Topics</span></span>](transformations-how-to-topics.md)
