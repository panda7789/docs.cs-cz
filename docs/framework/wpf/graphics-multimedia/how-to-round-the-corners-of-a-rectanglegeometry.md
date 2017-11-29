---
title: "Postupy: Zaoblení rohů RectangleGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cd857f7ce886095bcbe92ae57c350ce83bb5c7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="519af-102">Postupy: Zaoblení rohů RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="519af-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="519af-103">Má být zaokrouhleno rozích <xref:System.Windows.Media.RectangleGeometry>, nastavte jeho <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> vlastnosti na hodnotu větší než nula.</span><span class="sxs-lookup"><span data-stu-id="519af-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="519af-104">Větší hodnoty, oblejší obdélníku rozích.</span><span class="sxs-lookup"><span data-stu-id="519af-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="519af-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="519af-105">Example</span></span>  
 <span data-ttu-id="519af-106">Následující příklad ukazuje několik <xref:System.Windows.Media.RectangleGeometry> objektů pomocí různých <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="519af-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="519af-107"><xref:System.Windows.Media.RectangleGeometry> Zobrazení objektů pomocí <xref:System.Windows.Shapes.Path> elementy.</span><span class="sxs-lookup"><span data-stu-id="519af-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="519af-108">![Rámečky s jinou RadiusX &#47; RadiusY nastavení](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="519af-108">![Rectangles with different RadiusX&#47;RadiusY settings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="519af-109">Obdélníků se zaoblenými hranami</span><span class="sxs-lookup"><span data-stu-id="519af-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="519af-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="519af-110">See Also</span></span>  
 [<span data-ttu-id="519af-111">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="519af-111">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="519af-112">Vytváření kompozitních tvaru</span><span class="sxs-lookup"><span data-stu-id="519af-112">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="519af-113">Vytvoření obrazce pomocí Objekt PathGeometry</span><span class="sxs-lookup"><span data-stu-id="519af-113">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
