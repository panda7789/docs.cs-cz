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
ms.openlocfilehash: 7789f9aa94db32d3dc61ccf01ef9ddfe1e777a37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="5f626-102">Postupy: Vytvoření kompozitní kresby</span><span class="sxs-lookup"><span data-stu-id="5f626-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="5f626-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.DrawingGroup> vytvořit komplexní výkresy kombinací více <xref:System.Windows.Media.Drawing> objektů do jedné složené kreslení.</span><span class="sxs-lookup"><span data-stu-id="5f626-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f626-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f626-104">Example</span></span>  
 <span data-ttu-id="5f626-105">Následující příklad používá <xref:System.Windows.Media.DrawingGroup> vytvořit složené z <xref:System.Windows.Media.GeometryDrawing> a <xref:System.Windows.Media.ImageDrawing> objekty.</span><span class="sxs-lookup"><span data-stu-id="5f626-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="5f626-106">Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5f626-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="5f626-107">![Objekt DrawingGroup s více výkresů](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="5f626-107">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="5f626-108">Složené kreslení, která je vytvořená pomocí DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="5f626-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="5f626-109">Všimněte si šedého ohraničení, které znázorňuje hranice kreslení.</span><span class="sxs-lookup"><span data-stu-id="5f626-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="5f626-110">Můžete použít <xref:System.Windows.Media.DrawingGroup> pro použití <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> nastavení, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, nebo <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> výkresů obsahuje.</span><span class="sxs-lookup"><span data-stu-id="5f626-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="5f626-111">Protože <xref:System.Windows.Media.DrawingGroup> je také <xref:System.Windows.Media.Drawing>, může obsahovat jiné <xref:System.Windows.Media.DrawingGroup> objekty.</span><span class="sxs-lookup"><span data-stu-id="5f626-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="5f626-112">V následujícím příkladu je podobně jako v předchozím příkladu, s tím rozdílem, že používá další <xref:System.Windows.Media.DrawingGroup> objekty, které chcete použít dopady rastrového obrázku a masku krytí k některým z jeho kresby.</span><span class="sxs-lookup"><span data-stu-id="5f626-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="5f626-113">Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5f626-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="5f626-114">![Objekt DrawingGroup s více výkresů](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="5f626-114">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="5f626-115">Složené kreslení, který má více objektů DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="5f626-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="5f626-116">Všimněte si šedého ohraničení, které znázorňuje hranice kreslení.</span><span class="sxs-lookup"><span data-stu-id="5f626-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="5f626-117">Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete v části [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5f626-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f626-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f626-118">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [<span data-ttu-id="5f626-119">Kreslení objekty – přehled</span><span class="sxs-lookup"><span data-stu-id="5f626-119">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
