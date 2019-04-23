---
title: 'Postupy: Zaoblení rohů RectangleGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: eb2f173bedb903e12b2795264c684524cfa09825
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089130"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="b2b37-102">Postupy: Zaoblení rohů RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="b2b37-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="b2b37-103">K Zakulacení rohů <xref:System.Windows.Media.RectangleGeometry>, nastavte jeho <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> vlastnosti na hodnotu větší než nula.</span><span class="sxs-lookup"><span data-stu-id="b2b37-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="b2b37-104">Čím větší hodnoty, rohů udává větší zaoblení obdélníku.</span><span class="sxs-lookup"><span data-stu-id="b2b37-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2b37-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2b37-105">Example</span></span>  
 <span data-ttu-id="b2b37-106">Následující příklad ukazuje několik <xref:System.Windows.Media.RectangleGeometry> objekty s různými <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="b2b37-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="b2b37-107"><xref:System.Windows.Media.RectangleGeometry> Objekty jsou zobrazeny pomocí <xref:System.Windows.Shapes.Path> elementy.</span><span class="sxs-lookup"><span data-stu-id="b2b37-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="b2b37-108">![Obdélníků pomocí různých RadiusX&#47;RadiusY nastavení](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="b2b37-108">![Rectangles with different RadiusX&#47;RadiusY settings](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="b2b37-109">Obdélníky zaoblené rohy</span><span class="sxs-lookup"><span data-stu-id="b2b37-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b37-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2b37-110">See also</span></span>

- [<span data-ttu-id="b2b37-111">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="b2b37-111">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="b2b37-112">Vytvoření složeného tvaru</span><span class="sxs-lookup"><span data-stu-id="b2b37-112">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="b2b37-113">Vytvoření tvaru pomocí PathGeometry</span><span class="sxs-lookup"><span data-stu-id="b2b37-113">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
