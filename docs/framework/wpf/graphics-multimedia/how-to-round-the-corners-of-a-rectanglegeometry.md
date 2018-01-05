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
ms.workload: dotnet
ms.openlocfilehash: 92a51b3c610d3755583f8a39314f45d3980ee1bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>Postupy: Zaoblení rohů RectangleGeometry
Má být zaokrouhleno rozích <xref:System.Windows.Media.RectangleGeometry>, nastavte jeho <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> vlastnosti na hodnotu větší než nula. Větší hodnoty, oblejší obdélníku rozích.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje několik <xref:System.Windows.Media.RectangleGeometry> objektů pomocí různých <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> nastavení. <xref:System.Windows.Media.RectangleGeometry> Zobrazení objektů pomocí <xref:System.Windows.Shapes.Path> elementy.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![Rámečky s jinou RadiusX &#47; RadiusY nastavení](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")  
Obdélníků se zaoblenými hranami  
  
## <a name="see-also"></a>Viz také  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Vytvoření složeného tvaru](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Vytvoření tvaru pomocí PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
