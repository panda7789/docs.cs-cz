---
title: 'Postupy: Zaoblení rohů RectangleGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: 1a3ea08e4f54af117474cee23e6ac1041a1ed72b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648372"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="11799-102">Postupy: Zaoblení rohů RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="11799-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="11799-103">K Zakulacení rohů <xref:System.Windows.Media.RectangleGeometry>, nastavte jeho <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> vlastnosti na hodnotu větší než nula.</span><span class="sxs-lookup"><span data-stu-id="11799-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="11799-104">Čím větší hodnoty, rohů udává větší zaoblení obdélníku.</span><span class="sxs-lookup"><span data-stu-id="11799-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11799-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="11799-105">Example</span></span>  
 <span data-ttu-id="11799-106">Následující příklad ukazuje několik <xref:System.Windows.Media.RectangleGeometry> objekty s různými <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="11799-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="11799-107"><xref:System.Windows.Media.RectangleGeometry> Objekty jsou zobrazeny pomocí <xref:System.Windows.Shapes.Path> elementy.</span><span class="sxs-lookup"><span data-stu-id="11799-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="11799-108">![Obdélníků pomocí různých RadiusX&#47;RadiusY nastavení](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="11799-108">![Rectangles with different RadiusX&#47;RadiusY settings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="11799-109">Obdélníky zaoblené rohy</span><span class="sxs-lookup"><span data-stu-id="11799-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11799-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11799-110">See also</span></span>
- [<span data-ttu-id="11799-111">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="11799-111">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [<span data-ttu-id="11799-112">Vytvoření složeného tvaru</span><span class="sxs-lookup"><span data-stu-id="11799-112">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)
- [<span data-ttu-id="11799-113">Vytvoření tvaru pomocí PathGeometry</span><span class="sxs-lookup"><span data-stu-id="11799-113">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
