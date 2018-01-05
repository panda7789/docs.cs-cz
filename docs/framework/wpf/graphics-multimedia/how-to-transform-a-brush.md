---
title: "Postupy: Transformace štětce"
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
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ee517eb76877bb4e02c021061055b328597c517
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-transform-a-brush"></a>Postupy: Transformace štětce
Tento příklad ukazuje, jak k transformaci <xref:System.Windows.Media.Brush> objekty pomocí jejich vlastnosti dvě transformace: <xref:System.Windows.Media.Brush.RelativeTransform%2A> a <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 Následující příklady použití <xref:System.Windows.Media.RotateTransform> otočení obsah <xref:System.Windows.Media.ImageBrush> o 45 stupňů.  
  
 Následující obrázek ukazuje <xref:System.Windows.Media.ImageBrush> bez <xref:System.Windows.Media.RotateTransform>, s <xref:System.Windows.Media.RotateTransform> u <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost a <xref:System.Windows.Media.RotateTransform> u <xref:System.Windows.Media.Brush.Transform%2A> vlastnost.  
  
 ![Zdokonalit RelativeTransform a transformace nastavení](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Příklad  
 V prvním příkladu se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> objekt, jsou nastaveny na 0,5, která je relativní souřadnice centrálního bodu tohoto obsahu. V důsledku toho <xref:System.Windows.Media.ImageBrush> obsah otočí o jeho center.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 V druhém příkladu platí také <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.ImageBrush>; však tento příklad používá <xref:System.Windows.Media.Brush.Transform%2A> vlastnost místo <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost.  
  
 Otočit štětce o jeho center, v příkladu je nastaven <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> objekt, který chcete absolutní souřadnice. Vzhledem k tomu stopy vybarví obdélníku, která je 175 o 90 pixelů, je středový bod obdélníku (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Popis toho, jak <xref:System.Windows.Media.Brush.RelativeTransform%2A> a <xref:System.Windows.Media.Brush.Transform%2A> vlastnosti naleznete v tématech [štětce transformace přehled](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Kompletní příklad, najdete v části [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973). Další informace o štětce najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled transformace štětce](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
