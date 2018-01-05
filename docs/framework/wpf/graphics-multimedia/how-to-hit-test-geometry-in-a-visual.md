---
title: "Postupy: Spuštění geometrie testu ve vizuálním objektu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a990a43853e375c1c97f88dc6792932ad64c8d37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="3f652-102">Postupy: Spuštění geometrie testu ve vizuálním objektu</span><span class="sxs-lookup"><span data-stu-id="3f652-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="3f652-103">Tento příklad ukazuje, jak chcete provést test přístupů na vizuální objekt, který se skládá z jedné nebo více <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="3f652-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f652-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f652-104">Example</span></span>  
 <span data-ttu-id="3f652-105">Následující příklad ukazuje, jak načíst <xref:System.Windows.Media.DrawingGroup> z visual objektu, který používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="3f652-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="3f652-106">Ověření pozice pak provádí na vykreslovaných obsah jednotlivých kreslení v <xref:System.Windows.Media.DrawingGroup> k určení, které geometrie byl vybrán.</span><span class="sxs-lookup"><span data-stu-id="3f652-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f652-107">Ve většině případů byste použili <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda k určení, zda bod protíná některé z vykreslené obsah vizuál.</span><span class="sxs-lookup"><span data-stu-id="3f652-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="3f652-108"><xref:System.Windows.Media.Geometry.FillContains%2A> Metoda je přetížené metody, která umožňuje průchodu testu s použitím zadané <xref:System.Windows.Point> nebo <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="3f652-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="3f652-109">Pokud je vytažený geometry, tahu rozšířit mimo hranice výplně.</span><span class="sxs-lookup"><span data-stu-id="3f652-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="3f652-110">V takovém případě můžete chtít volání <xref:System.Windows.Media.Geometry.StrokeContains%2A> kromě <xref:System.Windows.Media.Geometry.FillContains%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f652-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="3f652-111">Můžete zadat taky <xref:System.Windows.Media.ToleranceType> používané pro účely Bézierovy sloučení.</span><span class="sxs-lookup"><span data-stu-id="3f652-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f652-112">Tato ukázka není vzít v úvahu žádné transformace nebo výstřižek, které mohou být použity u geometrie.</span><span class="sxs-lookup"><span data-stu-id="3f652-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="3f652-113">Kromě toho tato ukázka nebude fungovat s ovládacím prvkem stylem, vzhledem k tomu, že nemá žádné výkresy přímo s ním spojená.</span><span class="sxs-lookup"><span data-stu-id="3f652-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f652-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f652-114">See Also</span></span>  
 [<span data-ttu-id="3f652-115">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="3f652-115">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="3f652-116">Ověřování pozice pomocí objektu Geometry jako parametru</span><span class="sxs-lookup"><span data-stu-id="3f652-116">Hit Test Using Geometry as a Parameter</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
