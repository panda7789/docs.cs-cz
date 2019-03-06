---
title: 'Postupy: Vytvoření kombinované geometrie'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: c5ebe87abd4c2cf70f8fa17f1fcc773293f3ad27
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364785"
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="bbf2f-102">Postupy: Vytvoření kombinované geometrie</span><span class="sxs-lookup"><span data-stu-id="bbf2f-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="bbf2f-103">Tento příklad ukazuje způsob kombinování geometrií.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="bbf2f-104">Kombinování geometrií dvě, použijte <xref:System.Windows.Media.CombinedGeometry> objektu.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="bbf2f-105">Nastavte jeho <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> dvě geometrie sloučit, a nastavte vlastnosti <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> vlastnost, která určuje, jak geometrie se dá zkopírovat dohromady, k `Union`, `Intersect`, `Exclude`, nebo `Xor`.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="bbf2f-106">K vytvoření geometrie složený ze dvou nebo více geometrie, použijte <xref:System.Windows.Media.GeometryGroup>.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf2f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbf2f-107">Example</span></span>  
 <span data-ttu-id="bbf2f-108">V následujícím příkladu <xref:System.Windows.Media.CombinedGeometry> je definována s režim geometrie kombinování `Exclude`.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="bbf2f-109">Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="bbf2f-110">![Výsledky vyřadit kombinování režimu](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="bbf2f-110">![Results of the Exclude combine mode](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="bbf2f-111">Vyloučení kombinované geometrie</span><span class="sxs-lookup"><span data-stu-id="bbf2f-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="bbf2f-112">V následujícím kódu <xref:System.Windows.Media.CombinedGeometry> je definována s kombinování režimu `Intersect`.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="bbf2f-113">Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="bbf2f-114">![Výsledky Intersect kombinování režimu](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="bbf2f-114">![Results of the Intersect combine mode](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="bbf2f-115">Intersect kombinované geometrie</span><span class="sxs-lookup"><span data-stu-id="bbf2f-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="bbf2f-116">V následujícím kódu <xref:System.Windows.Media.CombinedGeometry> je definována s kombinování režimu `Union`.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="bbf2f-117">Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="bbf2f-118">![Výsledky sjednocení kombinování režimu](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="bbf2f-118">![Results of the Union combine mode](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="bbf2f-119">Sjednocení kombinované geometrie</span><span class="sxs-lookup"><span data-stu-id="bbf2f-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="bbf2f-120">V následujícím kódu <xref:System.Windows.Media.CombinedGeometry> je definována s kombinování režimu `Xor`.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="bbf2f-121">Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.</span><span class="sxs-lookup"><span data-stu-id="bbf2f-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="bbf2f-122">![Výsledky Xor kombinování režimu](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="bbf2f-122">![Results of the Xor combine mode](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="bbf2f-123">Xor kombinované geometrie</span><span class="sxs-lookup"><span data-stu-id="bbf2f-123">Combined Geometry Xor</span></span>
