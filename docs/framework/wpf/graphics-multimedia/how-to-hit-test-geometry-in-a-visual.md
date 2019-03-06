---
title: 'Postupy: Spuštění geometrie testu ve vizuálním objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: e51dd73a65666ffee5958325079e8f06f13ac61b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363797"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="793dd-102">Postupy: Spuštění geometrie testu ve vizuálním objektu</span><span class="sxs-lookup"><span data-stu-id="793dd-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="793dd-103">Tento příklad ukazuje, jak provádět ověření pozice ve vizuální objekt, který se skládá z jedné nebo více <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="793dd-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="793dd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="793dd-104">Example</span></span>  
 <span data-ttu-id="793dd-105">Následující příklad ukazuje, jak načíst <xref:System.Windows.Media.DrawingGroup> z visual objektu, který používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="793dd-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="793dd-106">Ověření pozice je pak provede na vykreslovaný obsah každého kreslení <xref:System.Windows.Media.DrawingGroup> k určení, které geometrie bylo dosaženo.</span><span class="sxs-lookup"><span data-stu-id="793dd-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="793dd-107">Ve většině případů byste použili <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodou ke zjištění, zda bod protíná některý vykreslený obsah vizuálu.</span><span class="sxs-lookup"><span data-stu-id="793dd-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="793dd-108"><xref:System.Windows.Media.Geometry.FillContains%2A> Je metoda přetížená metoda, která umožňuje spuštění testu s použitím zadaného <xref:System.Windows.Point> nebo <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="793dd-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="793dd-109">Pokud je vytažený geometrii, protože byl zdvih můžete rozšířit mimo hranice výplně.</span><span class="sxs-lookup"><span data-stu-id="793dd-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="793dd-110">V takovém případě můžete chtít volat <xref:System.Windows.Media.Geometry.StrokeContains%2A> kromě <xref:System.Windows.Media.Geometry.FillContains%2A>.</span><span class="sxs-lookup"><span data-stu-id="793dd-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="793dd-111">Můžete také zadat <xref:System.Windows.Media.ToleranceType> , který se používá pro účely sloučení Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="793dd-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="793dd-112">Tato ukázka není vezměte v úvahu všechny transformace nebo oříznutí, který může použít pro geometrii.</span><span class="sxs-lookup"><span data-stu-id="793dd-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="793dd-113">Kromě toho tato ukázka nebude fungovat u upravený ovládací prvek, protože nemá žádné kreslení přímo s ním spojená.</span><span class="sxs-lookup"><span data-stu-id="793dd-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793dd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="793dd-114">See also</span></span>
- [<span data-ttu-id="793dd-115">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="793dd-115">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="793dd-116">Ověřování pozice pomocí objektu Geometry jako parametru</span><span class="sxs-lookup"><span data-stu-id="793dd-116">Hit Test Using Geometry as a Parameter</span></span>](how-to-hit-test-using-geometry-as-a-parameter.md)
