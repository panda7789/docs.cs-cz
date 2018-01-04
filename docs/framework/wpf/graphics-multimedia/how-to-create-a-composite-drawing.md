---
title: "Postupy: Vytvoření kompozitní kresby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 424f77b076344ad86db992614175243d1473886d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="d3d87-102">Postupy: Vytvoření kompozitní kresby</span><span class="sxs-lookup"><span data-stu-id="d3d87-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="d3d87-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.DrawingGroup> vytvořit komplexní výkresy kombinací více <xref:System.Windows.Media.Drawing> objektů do jedné složené kreslení.</span><span class="sxs-lookup"><span data-stu-id="d3d87-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3d87-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3d87-104">Example</span></span>  
 <span data-ttu-id="d3d87-105">Následující příklad používá <xref:System.Windows.Media.DrawingGroup> vytvořit složené z <xref:System.Windows.Media.GeometryDrawing> a <xref:System.Windows.Media.ImageDrawing> objekty.</span><span class="sxs-lookup"><span data-stu-id="d3d87-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="d3d87-106">Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="d3d87-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="d3d87-107">![Objekt DrawingGroup s více výkresů](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="d3d87-107">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="d3d87-108">Složené kreslení, která je vytvořená pomocí DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="d3d87-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="d3d87-109">Všimněte si šedého ohraničení, které znázorňuje hranice kreslení.</span><span class="sxs-lookup"><span data-stu-id="d3d87-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="d3d87-110">Můžete použít <xref:System.Windows.Media.DrawingGroup> pro použití <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> nastavení, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, nebo <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> výkresů obsahuje.</span><span class="sxs-lookup"><span data-stu-id="d3d87-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="d3d87-111">Protože <xref:System.Windows.Media.DrawingGroup> je také <xref:System.Windows.Media.Drawing>, může obsahovat jiné <xref:System.Windows.Media.DrawingGroup> objekty.</span><span class="sxs-lookup"><span data-stu-id="d3d87-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="d3d87-112">V následujícím příkladu je podobně jako v předchozím příkladu, s tím rozdílem, že používá další <xref:System.Windows.Media.DrawingGroup> objekty, které chcete použít dopady rastrového obrázku a masku krytí k některým z jeho kresby.</span><span class="sxs-lookup"><span data-stu-id="d3d87-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="d3d87-113">Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="d3d87-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="d3d87-114">![Objekt DrawingGroup s více výkresů](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="d3d87-114">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="d3d87-115">Složené kreslení, který má více objektů DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="d3d87-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="d3d87-116">Všimněte si šedého ohraničení, které znázorňuje hranice kreslení.</span><span class="sxs-lookup"><span data-stu-id="d3d87-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="d3d87-117">Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete v části [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d3d87-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d87-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3d87-118">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [<span data-ttu-id="d3d87-119">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="d3d87-119">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
