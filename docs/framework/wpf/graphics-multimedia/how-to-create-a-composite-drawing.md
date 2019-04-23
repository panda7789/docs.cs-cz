---
title: 'Postupy: Vytvoření kompozitní kresby'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 0af7fbca593627ebe8cd102a02617a27eac50aa5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132467"
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="2d781-102">Postupy: Vytvoření kompozitní kresby</span><span class="sxs-lookup"><span data-stu-id="2d781-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="2d781-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.DrawingGroup> k vytvoření složitých drawings kombinací několika <xref:System.Windows.Media.Drawing> objekty do jednoho kompozitní kresby.</span><span class="sxs-lookup"><span data-stu-id="2d781-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d781-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d781-104">Example</span></span>  
 <span data-ttu-id="2d781-105">Následující příklad používá <xref:System.Windows.Media.DrawingGroup> vytvoření složeného vykreslování ze <xref:System.Windows.Media.GeometryDrawing> a <xref:System.Windows.Media.ImageDrawing> objekty.</span><span class="sxs-lookup"><span data-stu-id="2d781-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="2d781-106">Následující obrázek ukazuje výstup, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="2d781-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="2d781-107">![DrawingGroup – s použitím kreslení více](./media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="2d781-107">![A DrawingGroup with multiple drawings](./media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="2d781-108">Který je vytvořen pomocí DrawingGroup kompozitní kresby</span><span class="sxs-lookup"><span data-stu-id="2d781-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="2d781-109">Všimněte si šedé ohraničení, která ukazuje rozsah výkresu.</span><span class="sxs-lookup"><span data-stu-id="2d781-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="2d781-110">Můžete použít <xref:System.Windows.Media.DrawingGroup> použít <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> nastavení <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, nebo <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> kreslení obsahuje.</span><span class="sxs-lookup"><span data-stu-id="2d781-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="2d781-111">Protože <xref:System.Windows.Media.DrawingGroup> je také <xref:System.Windows.Media.Drawing>, mohou obsahovat jiné <xref:System.Windows.Media.DrawingGroup> objekty.</span><span class="sxs-lookup"><span data-stu-id="2d781-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="2d781-112">Následující příklad je podobný předchozí příklad, s tím rozdílem, že používá další <xref:System.Windows.Media.DrawingGroup> objektů použít některé z jeho drawings bitmapových efektů a masku neprůhlednosti.</span><span class="sxs-lookup"><span data-stu-id="2d781-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="2d781-113">Následující obrázek ukazuje výstup, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="2d781-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="2d781-114">![DrawingGroup – s použitím kreslení více](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="2d781-114">![A DrawingGroup with multiple drawings](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="2d781-115">Složené výkresu, který má více DrawingGroup – objekty</span><span class="sxs-lookup"><span data-stu-id="2d781-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="2d781-116">Všimněte si šedé ohraničení, která ukazuje rozsah výkresu.</span><span class="sxs-lookup"><span data-stu-id="2d781-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="2d781-117">Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete [kreslení objekty – přehled](drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d781-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d781-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d781-118">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [<span data-ttu-id="2d781-119">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="2d781-119">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
