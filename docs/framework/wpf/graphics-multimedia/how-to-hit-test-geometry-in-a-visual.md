---
title: 'Postupy: Ověření pozice objektu Geometry ve vizuálním objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 52b9b99b0af38d797e4a3c98dc0979211c930c1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923382"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="91b62-102">Postupy: Ověření pozice objektu Geometry ve vizuálním objektu</span><span class="sxs-lookup"><span data-stu-id="91b62-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="91b62-103">Tento příklad ukazuje, jak provést test přístupů na vizuální objekt, který se skládá z jednoho nebo více <xref:System.Windows.Media.Geometry> objektů.</span><span class="sxs-lookup"><span data-stu-id="91b62-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91b62-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="91b62-104">Example</span></span>  
 <span data-ttu-id="91b62-105">Následující příklad ukazuje, jak načíst <xref:System.Windows.Media.DrawingGroup> z vizuálního objektu, který <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> používá metodu.</span><span class="sxs-lookup"><span data-stu-id="91b62-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="91b62-106">Test volání se pak provede na vykresleném obsahu každého výkresu v <xref:System.Windows.Media.DrawingGroup> a určí, který geometrie se dosáhl.</span><span class="sxs-lookup"><span data-stu-id="91b62-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91b62-107">Ve většině případů byste použili <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodu k určení, zda se v bodě protínají jakékoli vykreslené obsahy vizuálu.</span><span class="sxs-lookup"><span data-stu-id="91b62-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="91b62-108">Metoda je přetížená metoda, která umožňuje volání testu pomocí zadaného <xref:System.Windows.Point> nebo <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.Geometry.FillContains%2A></span><span class="sxs-lookup"><span data-stu-id="91b62-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="91b62-109">Pokud je geometrie zatažena, tah lze zvětšit mimo hranice výplně.</span><span class="sxs-lookup"><span data-stu-id="91b62-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="91b62-110">V takovém případě může být vhodné volat <xref:System.Windows.Media.Geometry.StrokeContains%2A> <xref:System.Windows.Media.Geometry.FillContains%2A>kromě.</span><span class="sxs-lookup"><span data-stu-id="91b62-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="91b62-111">Můžete také zadat <xref:System.Windows.Media.ToleranceType> , který se používá pro účely plochého navýšení Bézierových křivek.</span><span class="sxs-lookup"><span data-stu-id="91b62-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91b62-112">Tato ukázka nebere v úvahu žádné transformace nebo oříznutí, které mohou být pro geometrii aplikovány.</span><span class="sxs-lookup"><span data-stu-id="91b62-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="91b62-113">Kromě toho tato ukázka nebude fungovat se stylem ovládacího prvku, protože nemá přímo přidružené kresby.</span><span class="sxs-lookup"><span data-stu-id="91b62-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91b62-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91b62-114">See also</span></span>

- [<span data-ttu-id="91b62-115">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="91b62-115">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="91b62-116">Ověřování pozice pomocí objektu Geometry jako parametru</span><span class="sxs-lookup"><span data-stu-id="91b62-116">Hit Test Using Geometry as a Parameter</span></span>](how-to-hit-test-using-geometry-as-a-parameter.md)
