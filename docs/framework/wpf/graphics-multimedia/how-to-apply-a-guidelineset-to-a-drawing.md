---
title: 'Postupy: Použití prvku GuidelineSet na kresbu'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 134236c5beca806b747d45f20764cc82ddd8a4e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699056"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a><span data-ttu-id="3a74c-102">Postupy: Použití prvku GuidelineSet na kresbu</span><span class="sxs-lookup"><span data-stu-id="3a74c-102">How to: Apply a GuidelineSet to a Drawing</span></span>
<span data-ttu-id="3a74c-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.GuidelineSet> k <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="3a74c-103">This example shows how to apply a <xref:System.Windows.Media.GuidelineSet> to a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
 <span data-ttu-id="3a74c-104"><xref:System.Windows.Media.DrawingGroup> Třída je jediným typem <xref:System.Windows.Media.Drawing> , který má <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3a74c-104">The <xref:System.Windows.Media.DrawingGroup> class is the only type of <xref:System.Windows.Media.Drawing> that has a <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> property.</span></span> <span data-ttu-id="3a74c-105">Použít <xref:System.Windows.Media.GuidelineSet> k jinému typu služby <xref:System.Windows.Media.Drawing>, ho přidat do <xref:System.Windows.Media.DrawingGroup> a následně použít <xref:System.Windows.Media.GuidelineSet> do vaší <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="3a74c-105">To apply a <xref:System.Windows.Media.GuidelineSet> to another type of <xref:System.Windows.Media.Drawing>, add it to a <xref:System.Windows.Media.DrawingGroup> and then apply the <xref:System.Windows.Media.GuidelineSet> to your <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a74c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a74c-106">Example</span></span>  
 <span data-ttu-id="3a74c-107">Následující příklad vytvoří dva <xref:System.Windows.Media.DrawingGroup> objekty, které jsou téměř shodné; jediným rozdílem je: druhý <xref:System.Windows.Media.DrawingGroup> má <xref:System.Windows.Media.GuidelineSet> a není první.</span><span class="sxs-lookup"><span data-stu-id="3a74c-107">The following example creates two <xref:System.Windows.Media.DrawingGroup> objects that are almost identical; the only difference is: the second <xref:System.Windows.Media.DrawingGroup> has a <xref:System.Windows.Media.GuidelineSet> and the first does not.</span></span>  
  
 <span data-ttu-id="3a74c-108">Výstup z příkladu ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="3a74c-108">The following illustration shows the output from the example.</span></span> <span data-ttu-id="3a74c-109">Protože vykreslování rozdíl mezi těmito dvěma <xref:System.Windows.Media.DrawingGroup> objekty se proto malý, jsou části výkresů zvětšené.</span><span class="sxs-lookup"><span data-stu-id="3a74c-109">Because the rendering difference between the two <xref:System.Windows.Media.DrawingGroup> objects is so subtle, portions of the drawings are enlarged.</span></span>  
  
 <span data-ttu-id="3a74c-110">![DrawingGroup – a nemusíte GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span><span class="sxs-lookup"><span data-stu-id="3a74c-110">![A DrawingGroup with and without a GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3a74c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a74c-111">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [<span data-ttu-id="3a74c-112">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="3a74c-112">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
